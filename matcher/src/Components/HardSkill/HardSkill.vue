<template>
  <div class="checkbox-container" :class="{'icon-active': status}">
    <p>{{skill}}</p>
    <input type="checkbox" @click="getSkill" name="skill" :value="skill">
  </div>
</template>
<script>
export default {
  props: ["skill",'getSkill'],
  data: function(){
    return {
      status: false
    }
  }
};
</script>
<style scoped>
.checkbox-container {
  padding: 10px;
  border-radius: 15px;
  text-align: center;
  display: inline-table;
  width: 180px;
  margin: 10px 25px 10px 0px;
}
.checkbox-container input {
  display: block;
   margin: 0 auto;
}
.checkbox-container i {
  position: relative;
  padding: 10px
}
.checkbox-container i::before {
  font-size: 50px;
}
.checkbox-container p {
  text-align: center;
}
.checkbox--icon {
  display: inline;
}
.icon-active {
  color: white;
  background: #0f1941;
  transition: 1s;
}
.icon-active p {
  color: white;
  transition: 1s;
}
</style>
