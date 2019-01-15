<template>
  <div class="container">
    <Logo/>
    <div class="Bread-Crumbs" v-if="currentPage>0">
      <bread-crumb
        v-for="(pageNumber,index) in pageNumbers"
        :key="index"
        :pageNumber="pageNumber"
        :isActive="pageNumber==currentPage"
        @click.native="goToPageNumber(pageNumber)"
      />
    </div>
    <IntroductionPage v-show="currentPage==0"/>
    <wie-ben-ik v-show="currentPage==1" :hobbies="hobbies" :icons="icons"/>
    <leer-stijle-page :questions="questions" v-show="currentPage==2"/>
    <werk v-show="currentPage==3" :skills="skills" :locations="locations"/>
    <start-button text="start" v-show="currentPage==0" :onClick="goToNextPage"/>
    <previous-button text="previous" v-if="currentPage>1" :onClick="goToPreviousPage"/>
    <next-button
      :text="currentPage==4?'Match':'next'"
      v-show="currentPage>0"
      :onClick="goToNextPage"
    />
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
import data from "./data.json";
import LeerStijlePage from "./Pages/LeerStijlPage/LeerStijlPage";
import dataToCompare from "./dataToCompare";

export default {
  components: {
    IntroductionPage: IntroductionPage,
    WieBenIk: WieBenIk,
    Werk: Werk,
    previousButton: Button,
    nextButton: Button,
    startButton: Button,
    Logo: Logo,
    BreadCrumb: BreadCrumb,
    LeerStijlePage: LeerStijlePage,
    matchButton: Button
  },
  name: "app",
  data() {
    return {
      currentPage: 0,
      pageNumbers: [1, 2, 3, 4, 5],
      questions: data.questions,
      hobbies: data.hobbies,
      icons: data.hobbyIcons,
      dataToCompare: dataToCompare,
      skills: data.skills,
      locations: data.locations,
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
      },
      result: []
    };
  },
  methods: {
    goToNextPage() {
      if (this.currentPage < 6) {
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
          console.log(softSkills);

          this.person.processiveData.softSkills = softSkills;
        });
        if (
          this.person.processiveData.hardSkills.length > 0 &&
          this.person.processiveData.softSkills
        ) {
          this.Match();
        }
      }
    },
    emitMethods() {},
    goToPreviousPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
    goToPageNumber(index) {
      this.currentPage = index;
    },
    Match() {
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
        if (this.person.processiveData.location == company.Location)
          locationMatch++;
        this.result[index] = {
          companyName: company.CompanyName,
          totalMatch: softSkillMatch + hardSkillMatch + locationMatch
        };
        console.log("softSkillMatch", softSkillMatch);
        console.log("hardSkillMatch", hardSkillMatch);
        console.log("locationMatch", locationMatch);

        softSkillMatch = 0;
        hardSkillMatch = 0;
        locationMatch = 0;
      });
    }
  }
};
</script>
