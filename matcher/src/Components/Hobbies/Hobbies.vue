
<template>
  <div>
    <Label>{{label}}</Label>
    <ul>
      <Hobby v-for="(hobby,index) in hobbies" 
      :key="index" 
      :hobby="hobby"
      :getHobby="getHobby" 
      />
    </ul>
  </div>
</template>

<script>
import Hobby from "../Hobby/Hobby";
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      filledHobbies:[]
    };
  },
  components: {
    Hobby: Hobby
  },
  props: ["label", "hobbies"],
  methods: {
    getHobby(event) {
      if (event.target.checked) {
        this.filledHobbies.push(event.target.value);
      } else {
        this.filledHobbies = this.filledHobbies.filter(a => a != event.target.value);
      }
      EventBus.$emit("hobbyChanged", this.filledHobbies);
    }
  }
};
</script>

<style>
</style>
