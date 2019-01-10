
<template>
  <div>
    <Label>{{label}}</Label>
    <input type="checkbox" @click="getHobby" name="hobby" value="sporten">
    <label for="hobby">sporten</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="muziek">
    <label for="hobby">muziek</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="fotograferen">
    <label for="hobby">fotograferen</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="koken">
    <label for="hobby">koken</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="tekenen">
    <label for="hobby">tekenen</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="lezen">
    <label for="hobby">lezen</label>
  </div>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      hobbies: []
    };
  },
  props: ["label"],
  methods: {
    getHobby(event) {
      if (event.target.checked) {
        this.hobbies.push(event.target.value);
      } else {
        this.hobbies = this.hobbies.filter(a => a != event.target.value);
      }
      EventBus.$emit("hobyChanged", this.hobbies);
    }
  }
};
</script>

<style>
</style>
