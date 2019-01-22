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
              :addHobby="addHobby"
              :deleteHobby="deleteHobby"
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
      filledHobbies: []
    };
  },
  components: {
    Hobby: Hobby
  },
  props: ["label", "hobbies", "icons"],
  methods: {
    addHobby(hobby) {
      if (!this.hobbyExistsInTheList(hobby)) {
        this.filledHobbies.push(hobby);
        EventBus.$emit("hobbyChanged", this.filledHobbies);
      }
    },
    deleteHobby(hobby) {
      if (this.hobbyExistsInTheList(hobby)) {
        this.filledHobbies = this.filledHobbies.filter(a => a != hobby);
        EventBus.$emit("hobbyChanged", this.filledHobbies);
      }
    },
    hobbyExistsInTheList(hobby) {
      return this.filledHobbies.includes(hobby);
    }
  }
};
</script>
<style>
</style>