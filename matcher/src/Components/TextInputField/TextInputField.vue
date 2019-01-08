<template>
<div>
<Label>{{label}}</Label>
  <input type="text" :whatToChange="whatToChange" @change="changeName">
</div>
</template>
<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      whatToChange: ""
    };
  },
  props: ["whatToChange",'label'],
  methods: {
    changeName(event) {
      if (this.whatToChange == "name") {
        EventBus.$emit("nameChanged", event.target.value);
      } else {
        EventBus.$emit("SelfInfoChanged", event.target.value);
      }
    }
  }
};
</script>
