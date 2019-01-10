<template>
  <li>
    <Label>{{question}}</Label>
    <input type="radio" v-model="selectedOption" @click="getSkill" :value="option1">
    <input type="radio" v-model="selectedOption" @click="getSkill" :value="option2">
  </li>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      selectedOption: null,
      index: this.index,
    };
  },
  props: ["question", "option1", "option2", "getOption", "index"],
  methods: {
    getSkill: function(event) {
      if (event.target.checked) {
        this.selectedOption = event.target.value;
        this.getOption(this.index, this.selectedOption);
      }
    }
  }
};
</script>

<style>
</style>
