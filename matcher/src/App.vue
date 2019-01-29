<template>
  <div class="body--frame">
    <div class="container-fluid">
      <Logo @click.native="goToHomePage"/>
    </div>
    <div class="container">
      <BreadCrumbs
        :currentPage="currentPage"
        :pageNumbers="pageNumbers"
        :breadcrumbIcons="breadcrumbIcons"
        :breadcrumbSpeechBubbles="breadcrumbSpeechBubbles"
        :goToPageNumber="goToPageNumber"
      />
      <IntroductionPage v-show="currentPage==0"/>
      <wie-ben-ik v-show="currentPage==1" :hobbies="hobbies" :icons="icons"/>
      <leer-stijle-page :questions="questions" v-show="currentPage==2"/>
      <werk v-show="currentPage==3" :skills="skills" :skillIcons="skillIcons" :locations="locations"/>
      <!-- LoadingPage wordt nu opgeroepen als een paginanummer, maar dit is puur om dit als een demo te laten zien. 
        In de final version is LoadingPage natuurlijk niet altijd na pagina drie, maar zal altijd worden gebruikt op moment 
      dat er wordt gewacht op data, bijv. wanneer er data moet worden gefetched vanuit een API.-->
      <LoadingPage v-if="currentPage==4" :next="goToNextPage"/>
      <match-page v-show="currentPage==5" :results="[...results]"/>
      <result-profile-page
        v-show="currentPage==6"
        :results="[...results]"
        :name="person.unProcessedData.name"
        :oneliner="person.unProcessedData.info"
        :hobbies="person.unProcessedData.hobbies"
        :setHobbyClassName="setHobbyClassName"
        :skills="person.processiveData.hardSkills"
        :setHardskillClassName="setHardskillClassName"
      />
      <result-page v-show="currentPage==7" :results="[...results]"/>
      <div class="button__align--center">
        <start-button text="start" v-show="currentPage==0" :onClick="goToNextPage"/>
        <previous-button
          text="previous"
          v-if="currentPage>1 && currentPage<8 && currentPage!=4 && currentPage!=5 && currentPage!=6"
          :onClick="goToPreviousPage"
        />
        <next-button
          text="next"
          v-show="currentPage>0 && currentPage<7 && currentPage!=3 && currentPage!=4"
          :onClick="goToNextPage"
        />
        <match-button text="match" v-if="currentPage == 3" :onClick="goToNextPage"/>
      </div>
    </div>
    <div class="container-fluid">
      <Footer/>
    </div>
  </div>
</template>

<script>
import { EventBus } from "./Event-bus";
import IntroductionPage from "./Pages/IntroductionPage/Introduction";
import WieBenIk from "./Pages/WieBenIk/WieBenIk";
import Werk from "./Pages/WerkPage/Werk";
import Button from "./Components/Buttons/Button";
import Logo from "./Components/Logo/Logo";
import BreadCrumbs from "./Components/BreadCrumbs/BreadCrumbs";
import Footer from "./Components/Footer/Footer";
import data from "./data.json";
import LeerStijlePage from "./Pages/LeerStijlPage/LeerStijlPage";
import dataToCompare from "./dataToCompare";
import ResultPage from "./Pages/ResultPage/ResultPage";
import MatchPage from "./Pages/MatchPage/MatchPage";
import LoadingPage from "./Pages/LoadingPage/LoadingPage";
import ResultProfilePage from "./Pages/ResultProfilePage/ResultProfilePage";

export default {
  components: {
    IntroductionPage: IntroductionPage,
    WieBenIk: WieBenIk,
    Werk: Werk,
    previousButton: Button,
    nextButton: Button,
    startButton: Button,
    matchButton: Button,
    Logo: Logo,
    BreadCrumbs: BreadCrumbs,
    Footer: Footer,
    LeerStijlePage: LeerStijlePage,
    matchButton: Button,
    ResultPage: ResultPage,
    MatchPage: MatchPage,
    LoadingPage: LoadingPage,
    ResultProfilePage: ResultProfilePage
  },
  name: "app",
  data() {
    return {
      currentPage: 0,
      pageNumbers: [1, 2, 3, 4, 5, 6, 7],
      questions: data.questions,
      hobbies: data.hobbies,
      icons: data.hobbyIcons,
      breadcrumbIcons: data.breadcrumbIcons,
      breadcrumbSpeechBubbles: data.breadcrumbSpeechBubbles,
      dataToCompare: dataToCompare,
      skills: data.skills,
      skillIcons: data.skillIcons,
      locations: data.locations,
      results: [],
      person: {
        unProcessedData: {
          name: "",
          image: null,
          hobbies: [],
          info: ""
        },
        processiveData: {
          softSkills: [],
          hardSkills: [],
          location: ""
        }
      }
    };
  },

  methods: {
    goToNextPage() {
      if (this.currentPage < 8) {
        this.currentPage++;
        EventBus.$on("nameChanged", name => {
          this.person.unProcessedData.name = name;
        });
        EventBus.$on("ChooseLocation", location => {
          this.person.processiveData.location = location;
        });
        EventBus.$on("imageTaken", image => {
          this.person.unProcessedData.image = image;
        });
        EventBus.$on("hobbyChanged", hobbies => {
          this.person.unProcessedData.hobbies = hobbies;
        });
        EventBus.$on("SelfInfoChanged", info => {
          this.person.unProcessedData.info = info;
        });
        EventBus.$on("hardSkillsChanged", hardSkills => {
          this.person.processiveData.hardSkills = hardSkills;
        });
        EventBus.$on("SoftSkillsDone", softSkills => {
          this.person.processiveData.softSkills = softSkills;
        });
        if (
          this.person.processiveData.hardSkills.length > 0 &&
          this.person.processiveData.softSkills.length == 10 &&
          this.person.processiveData.location != ""
        ) {
          this.Match();
        }
      }
    },
    emitMethods() {},

    setHobbyClassName(hobby) {
      return data.hobbyIcons[data.hobbies.indexOf(hobby)];
    },
    setHardskillClassName(skill) {
      return data.skillIcons[data.skills.indexOf(skill)];
    },
    goToPreviousPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
    goToPageNumber(index) {
      this.currentPage = index;
    },
    Match: function() {
      let softSkillMatch = 0;
      let hardSkillMatch = 0;
      let locationMatch = 0;
      let personHardSkills = this.person.processiveData.hardSkills;
      let personSoftSkills = this.person.processiveData.softSkills;
      this.dataToCompare.forEach((company, index) => {
        company.SoftSkills.forEach(companySoftSkill => {
          personSoftSkills.forEach(personSoftSkill => {
            if (companySoftSkill == personSoftSkill) {
              softSkillMatch++;
            }
          });
        });
        company.HardSkills.forEach(companyHardSkill => {
          personHardSkills.forEach(personHardSkill => {
            if (companyHardSkill == personHardSkill) {
              hardSkillMatch++;
            }
          });
        });
        if (this.person.processiveData.location == company.Location) {
          locationMatch++;
        }
        this.results[index] = {
          companyName: company.CompanyName,
          totalMatch: softSkillMatch + hardSkillMatch + locationMatch
        };
        softSkillMatch = 0;
        hardSkillMatch = 0;
        locationMatch = 0;
      });
    },
    goToHomePage() {
      this.currentPage = 0;
    }
  }
};
</script>
