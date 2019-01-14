<template>
  <li>
    <Label>{{hobby}}</Label>
    <input type="checkbox" @click="getHobby" name="hobby" :value="hobby">
  </li>
</template>

<script>
export default {
    props:['hobby','getHobby']
};
</script>

<style>
</style>
