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
    <wie-ben-ik v-show="currentPage==1"/>
    <werk v-show="currentPage==2"/>
    <start-button text="start" v-show="currentPage==0" :onClick="goToNextPage"/>
    <previous-button text="previous" v-if="currentPage>1" :onClick="goToPreviousPage"/>
    <next-button text="next" v-show="currentPage>0" :onClick="goToNextPage"/>
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
export default {
  components: {
    IntroductionPage: IntroductionPage,
    WieBenIk: WieBenIk,
    Werk: Werk,
    previousButton: Button,
    nextButton: Button,
    startButton: Button,
    Logo: Logo,
    BreadCrumb: BreadCrumb
  },
  name: "app",
  data() {
    return {
      currentPage: 0,
      pageNumbers: [1, 2, 3, 4, 5],
      questions: data.questions,
      person: {
        name: "",
        image: null,
        hobies: [],
        info: "",
        skills: []
      }
    };
  },
  methods: {
    goToNextPage() {
      if (this.currentPage < 6) {
        this.currentPage++;
        EventBus.$on("nameChanged", name => {
          this.person.name = name;
        });
        EventBus.$on("imageTaken", image => {
          this.person.image = image;
        });
        EventBus.$on("hobyChanged", hobies => {
          this.person.hobies = hobies;
        });
        EventBus.$on("SelfInfoChanged", info => {
          this.person.info = info;
        });
        EventBus.$on("skillChanged", skills => {
          this.person.skills = skills;
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
    }
  }
};
</script>
