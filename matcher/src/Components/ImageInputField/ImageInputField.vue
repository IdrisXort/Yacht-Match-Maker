<template>
<div>
<Label>{{label}}</Label>
  <input type="file" accept="image/png, image/jpeg" @change="getImage">
</div>
</template>
<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      image: null
    };
  },
  props: ['label'],
  methods: {
    getImage(event) {
      this.image = event.target.value;

      EventBus.$emit("imageTaken", this.image);
    }
  }
};
</script>
