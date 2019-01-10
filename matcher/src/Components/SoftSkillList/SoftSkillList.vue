<template>
  <ul>
    <soft-skill
      v-for="(question,index) in questions"
      :key="index"
      :question="question.question"
      :option1="question.option1"
      :option2="question.option2"
      :index="index"
      :getOption="getOption"
    />
  </ul>
</template>

<script>
import {EventBus} from '../../Event-bus';
import SoftSkill from "../SoftSkill/SoftSkill";
export default {
  props: ["questions"],
  components: {
    SoftSkill: SoftSkill
  },
  data() {
    return {
      options: [],
      chosenNumber: 0
    };
  },
  methods: {
    getOption(index, option) {
      if (typeof this.options[index] == "undefined") {
        this.chosenNumber++;
      }
      this.options[index] = option;
      if(this.chosenNumber==10){
        EventBus.$emit('SoftSkillsDone',this.options);
      }
    }
  }
};
</script>

<style>
</style>
