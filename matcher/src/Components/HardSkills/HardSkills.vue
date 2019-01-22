<template>
  <div>
    <div>
      <div class="col-11">
        <div class="row">
            <label>{{label}}</label>
            <div>
              <hard-skill v-for="(skill,index) in skills" 
              :key="index" 
              :skill="skill"
              :getSkill="getSkill"              
              />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import HardSkill from '../HardSkill/HardSkill'
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      filledSkills:[]
    };
  },
  components: {
    HardSkill: HardSkill
  },
  props: ["label", "skills"],
  methods: {
    getSkill(event) {
      if (event.target.checked) {
        this.filledSkills.push(event.target.value);
      } else {
        this.filledSkills = this.filledSkills.filter(a => a != event.target.value);
      }
      EventBus.$emit("hardSkillsChanged", this.filledSkills);
    }
  }
};
</script>
<style>
</style>