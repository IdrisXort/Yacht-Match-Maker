<template>
  <div>
    <Label>{{label}}</Label>
    <div>
      <div class="container no-padding-left">
        <div class="col-sm-9 no-padding-left">
          <div class="row">
            <div class="col-sm no-padding-left">
              <Hobby v-for="(hobby,index) in hobbies" 
              :key="index" 
              :hobby="hobby"
              :icon="icons[index]"
              :getHobby="getHobby"
              @click.native="getHobby"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
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
  props: ["label", "hobbies", "icons"],
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