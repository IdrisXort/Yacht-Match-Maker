<template>
  <ul>
    <soft-skill
      v-for="(question,index) in questions"
      :key="index"
      :question="question.question"
      :option1="question.option1"
      :option2="question.option2"
      :index="index"
      @click.native="handleClick"
    />
  </ul>
</template>

<script>
import SoftSkill from "../SoftSkill/SoftSkill";
export default {
  props: ["questions"],
  components: {
    SoftSkill: SoftSkill
  },
  data() {
    return {
      SoftSkills: []
    };
  },
  methods: {
    handleClick(event) {
      console.log(event.target);



      
    }
  }
};
</script>

<style>
</style>
