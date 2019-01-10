<template>
  <soft-skill-list :questions="questions"/>
</template>

<script>
import SoftSkillList from "../../Components/SoftSkillList/SoftSkillList";
export default {
  props: ["questions"],
  components: {
    SoftSkillList: SoftSkillList
  }
};
</script>

<style>
</style>
