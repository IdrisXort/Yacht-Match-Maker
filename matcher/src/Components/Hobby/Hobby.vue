<template>
  <div class="checkbox-container" :class="{'icon-active': status}">
    <p>{{hobby}}</p>
     <i :class="icon"></i>
    <input type="checkbox" @click="changeStatus" name="hobby" :value="hobby">
  </div>
</template>
<script>
export default {
  props: ["hobby", "getHobby", "icon"],
  data: function(){
    return {
      status: false
    }
  },
  methods: {
    changeStatus() {
      this.status = !this.status;
    }
  }
};
</script>
<style>
.checkbox-container {
  padding: 15px;
  border-radius: 15px;
  text-align: center;
  display: inline-table;
  width: 180px;
  margin: 15px 30px 15px 0px;
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
  font-size: 100px;
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
