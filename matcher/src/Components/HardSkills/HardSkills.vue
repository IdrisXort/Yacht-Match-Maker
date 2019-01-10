
<template>
  <div>
    <Label>{{label}}</Label>
    <input type="checkbox" @click="getSkill" name="skill" value="C#">
    <label for="skill">C#</label>
    <input type="checkbox" @click="getSkill" name="skill" value="C++">
    <label for="skill">C++</label>
    <input type="checkbox" @click="getSkill" name="skill" value="HTML">
    <label for="skill">HTML</label>
    <input type="checkbox" @click="getSkill" name="skill" value="CSS">
    <label for="skill">CSS</label>
    <input type="checkbox" @click="getSkill" name="skill" value="Javascript">
    <label for="skill">Javascript</label>
    <input type="checkbox" @click="getSkill" name="skill" value="PHP">
    <label for="skill">PHP</label>
    <input type="checkbox" @click="getSkill" name="skill" value="SQL">
    <label for="skill">SQL</label>
    <input type="checkbox" @click="getSkill" name="skill" value="Python">
    <label for="skill">Python</label>
    <input type="checkbox" @click="getSkill" name="skill" value="Java">
    <label for="skill">Java</label>
    <input type="checkbox" @click="getSkill" name="skill" value="SiteCore">
    <label for="skill">SiteCore</label>
  </div>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      skills: []
    };
  },
  props: ["label"],
  methods: {
    getSkill(event) {
      if (event.target.checked) {
        this.skills.push(event.target.value);
      } else {
        this.skills = this.skills.filter(a => a != event.target.value);
      }
      EventBus.$emit("skillChanged", this.skills);
      console.log(this.skills, 'skillll');
    }
  }
};
</script>

<style>
</style>
