<template>
  <div class="body--frame">
    <div class="container-fluid">
      <Logo @click.native="goToHomePage"/>
    </div>
    <div class="container">
      <div class="Bread-Crumbs" v-if="currentPage>0">
        <bread-crumb
          v-for="(pageNumber,index) in pageNumbers"
          :key="index"
          :pageNumber="pageNumber"
          :isActive="pageNumber==currentPage"
          @click.native="goToPageNumber(pageNumber)"
          v-show="currentPage<4"
        />
      </div>
      <IntroductionPage v-show="currentPage==0"/>
      <wie-ben-ik v-show="currentPage==1" :hobbies="hobbies" :icons="icons"/>
      <leer-stijle-page :questions="questions" v-show="currentPage==2"/>
      <werk v-show="currentPage==3" :skills="skills" :locations="locations"/>
      <LoadingPage v-if="currentPage==4" :next="goToNextPage"/>
      <match-page v-show="currentPage==5" :results="[...results]"/>
      <result-page v-show="currentPage==6" :results="[...results]"/>
      <result-profile-page
        v-show="currentPage==7"
        :results="[...results]"
        :name="person.unProcessedData.name"
        :oneliner="person.unProcessedData.info"
        :hobbies="person.unProcessedData.hobbies"
        :setHobbyClassName="setHobbyClassName"
      />
      <div class="button__align--center">
        <start-button text="start" v-show="currentPage==0" :onClick="goToNextPage"/>
        <previous-button
          text="previous"
          v-if="currentPage>1 && currentPage<6 && currentPage!=4"
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
import BreadCrumb from "./Components/BreadCrumbs/BreadCrumb";
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
    BreadCrumb: BreadCrumb,
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
      dataToCompare: dataToCompare,
      skills: data.skills,
      locations: data.locations,
      results: [],
      validations: {
        name: false,
        selfInfo: false,
        image: false,
        hobbies: false,
        softSkills: false,
        companySize: false,
        location: false,
        hardSkills: false
      },
      inCompleted: [],
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
          location: "",
          companySize:''
        }
      }
    };
  },

  methods: {
    goToNextPage() {
      if (this.currentPage < 8) {
        this.currentPage++;
        EventBus.$on("nameChanged", name => {
          if (name != "") {
            this.person.unProcessedData.name = name;
            this.validations.name = true;
          } else {
            this.validations.name = false;
          }
        });
        EventBus.$on("ChooseLocation", location => {
          if (location != "") {
            this.person.unProcessedData.location = location;
            this.validations.location = true;
          } else {
            this.validations.location = false;
          }
        });
        EventBus.$on("imageTaken", image => {
          if (image != "") {
            this.person.unProcessedData.image = image;
            this.validations.image = true;
          } else {
            this.validations.image = false;
          }
        });
        EventBus.$on("companySizeChanged", companySize => {
                    if (companySize != "") {
            this.person.processiveData.companySize = companySize;
            this.validations.companySize = true;
          } else {
            this.validations.companySize = false;
          }
        });
        EventBus.$on("hobbyChanged", hobbies => {
          if (hobbies.length > 0) {
            this.person.unProcessedData.hobbies = hobbies;
            this.validations.hobbies = true;
          } else {
            this.validations.hobbies = false;
          }
        });
        EventBus.$on("SelfInfoChanged", info => {
          if (info != "") {
            this.person.unProcessedData.info = info;
            this.validations.info = true;
          } else {
            this.validations.info = false;
          }
        });
        EventBus.$on("hardSkillsChanged", hardSkills => {
          if (hardSkills.length > 0) {
            this.person.processiveData.hardSkills = hardSkills;
            this.validations.hardSkills = true;
          } else {
            this.validations.hardSkills = false;
          }
        });
        EventBus.$on("SoftSkillsDone", softSkills => {
          if (softSkills.length == 10) {
            this.person.processiveData.softSkills = softSkills;
            this.validations.softSkills = true;
          } else {
            this.validations.softSkills = false;
          }
        });
        this.whatIsNotComplete();
        if (this.isComplete()) {
          this.Match();
        }
      }
    },
    emitMethods() {},
    setHobbyClassName(hobby) {
      return data.hobbyIcons[data.hobbies.indexOf(hobby)];
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
    },
    isComplete() {
      return Object.values(this.validations).every(a => a == true);
    },
    whatIsNotComplete() {
      let arr = [];
      Object.values(this.validations).map((a, index) => {
        console.log(a,index)
        if (a == false) {
          arr.push(Object.keys(this.validations)[index])
        }
      });
      this.inCompleted=arr;
    }
  }
};
</script>
