<template>
  <div>
    <Logo/>
    <bread-crumb/>
    <IntroductionPage v-show="currentPage==0"/>
    <wie-ben-ik v-show="currentPage==1" />
    <werk v-show="currentPage==2"/>
    <previous-button text="previous" v-if="currentPage>1" :onClick="goToPreviousPage"/>
    <next-button
      :text="currentPage==0?'start':'next'"
      v-show="currentPage>-1"
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
import Logo from './Components/Logo/Logo';
import BreadCrumb from './Components/BreadCrumbs/BreadCrumb';
export default {
  components: {
    IntroductionPage: IntroductionPage,
    WieBenIk: WieBenIk,
    Werk: Werk,
    previousButton: Button,
    nextButton: Button,
    Logo:Logo,
    BreadCrumb:BreadCrumb
  },
  name: "app",
  data() {
    return {
      currentPage: 0,
      person: {
        name: "",
        image: null,
        hobies:[]
      }
    };
  },
  methods: {
    goToNextPage() {
      if (this.currentPage < 2) {
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
        
      }
    },
    goToPreviousPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    }
  }
};
</script>