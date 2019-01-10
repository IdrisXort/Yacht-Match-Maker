<template>
<div>
<Label>{{label}}</Label>
  <label class="image__field--button">
    <i class="fas fa-upload icon__left"></i>upload
    <input type="file" accept="image/png, image/jpeg" @change="getImage">
  </label>
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
<style>
  input[type="file"] {
    display: none;
  }
  .image__field--button {
    color:white;
    border:none;
    border-radius:6px;
    padding: 10px 20px;
    font-size: 16px;
    font-weight: 700;
    line-height: 25px;
    background-color: #192a56;
    cursor: pointer;
  } 

  .icon__left{
    font-size: 14px;
    margin-right: .5em;
  }
</style>

