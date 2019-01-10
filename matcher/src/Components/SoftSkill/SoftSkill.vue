<template>
  <li>
    <Label>{{question}}</Label>
    <input type="radio" v-model="selectedOption" :value="option1">
    <input type="radio" v-model="selectedOption" :value="option2">
  </li>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      selectedOption: null
    };
  },
  props: ["question", "option1", "option2"],
  methods: {
    getSkill: function(event) {
      if (event.target.checked) {
        EventBus.$emit("optionChanged", event.target.value);
      }
    }
  }
};
</script>

<style>
</style>
