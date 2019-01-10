<template>
  <li>
    <Label>{{hoby}}</Label>
    <input type="checkbox" @click="getHobby" name="hobby" :value="hoby">
  </li>
</template>

<script>
export default {
    props:['hoby','getHobby']
};
</script>

<style>
</style>
