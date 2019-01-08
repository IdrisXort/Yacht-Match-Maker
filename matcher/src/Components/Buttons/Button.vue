<template>
  <button class="btn button" @click="onClick">{{text}}</button>
</template>
<script>
export default {
  props: ["onClick", "text"],
  data() {
    return {};
  }
};
</script>
<style>
  .button {
    background-color: green;
  } 
</style>