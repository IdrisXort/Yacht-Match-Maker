<template>
  <div>
    <div>
      <div class="container no-padding-left">
        <div class="col-sm-9 no-padding-left">
          <div class="row">
              <label>{{label}}</label>
              <div>
                <hard-skill v-for="(skill,index) in skills" 
                :key="index" 
                :skill="skill"
                :addSkill="addSkill"
                :deleteSkill="deleteSkill"  
                :skillIcons="skillIcons[index]"            
                />
              </div>
            </div>
          </div>
        </div> 
      </div>
  </div>
</template>
<script>
import HardSkill from "../HardSkill/HardSkill";
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      filledSkills: []
    };
  },
  components: {
    HardSkill: HardSkill
  },
  props: ["label", "skills", "skillIcons"],
  methods: {
    getSkill(event) {
      if (event.target.checked) {
        this.filledSkills.push(event.target.value);
      } else {
        this.filledSkills = this.filledSkills.filter(
          a => a != event.target.value
        );
      }
      EventBus.$emit("hardSkillsChanged", this.filledSkills);
    },

    addSkill(skill) {
      if (!this.skillExistsInTheList(skill)) {
        this.filledSkills.push(skill);
        EventBus.$emit("hardSkillsChanged", this.filledSkills);
      }
    },
    deleteSkill(skill) {
      if (this.skillExistsInTheList(skill)) {
        this.filledSkills = this.filledSkills.filter(a => a != skill);
        EventBus.$emit("hardSkillsChanged", this.filledSkills);
      }
    },
    skillExistsInTheList(skill) {
      return this.filledSkills.includes(skill);
    }
  }
};
</script>
<style>
</style>