
<template>
  <div>
    <Label>{{label}}</Label>
    <ul>
      <Hoby v-for="(hoby,index) in hobies" 
      :key="index" 
      :hoby="hoby"
      :getHobby="getHobby" 
      />
    </ul>
  </div>
</template>

<script>
import Hoby from "../Hoby/Hoby";
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      filledHobies:[]
    };
  },
  components: {
    Hoby: Hoby
  },
  props: ["label", "hobies"],
  methods: {
    getHobby(event) {
      if (event.target.checked) {
        this.filledHobies.push(event.target.value);
      } else {
        this.filledHobies = this.filledHobies.filter(a => a != event.target.value);
      }
      EventBus.$emit("hobyChanged", this.filledHobies);
    }
  }
};
</script>

<style>
</style>
