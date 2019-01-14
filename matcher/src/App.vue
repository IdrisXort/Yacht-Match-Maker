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
    <werk v-show="currentPage==3"/>
    <start-button text="start" v-show="currentPage==0" :onClick="goToNextPage"/>
    <previous-button text="previous" v-if="currentPage>1" :onClick="goToPreviousPage"/>
    <next-button text="next" v-show="currentPage>0" :onClick="goToNextPage"/>
    <match-button v-show="currentPage==4" text="match" :onClick="Match"/>
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
      icons:data.hobbyIcons,
      dataToCompare: dataToCompare,
      person: {
        unProcessedData: {
          name: "",
          image: null,
          hobbies: [],
          info: ""
        },
        processiveData: {
          softSkills: []
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
        EventBus.$on("imageTaken", image => {
          this.person.unProcessedData.image = image;
        });
        EventBus.$on("hobbyChanged", hobbies => {
          this.person.unProcessedData.hobbies = hobbies;
        });
        EventBus.$on("SelfInfoChanged", info => {
          this.person.unProcessedData.info = info;
        });
        EventBus.$on("SoftSkillsDone", softSkills => {
          console.log(softSkills);

          this.person.processiveData.softSkills = softSkills;
        });
      }
    },
    goToPreviousPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
    goToPageNumber(index) {
      this.currentPage = index;
    },
    Match() {
      let match = 0;
      let personSoftSkills = this.person.processiveData.softSkills;
      this.dataToCompare.forEach(company => {
        company.SoftSkills.forEach(companySkill => {
          personSoftSkills.forEach(personSkill => {
            if (companySkill == personSkill) {
              match++;
            }
          });
        });
        this.result.push({ companyName: company.CompanyName, matches: match });
        match = 0;
      });
    }
  }
};
</script>
