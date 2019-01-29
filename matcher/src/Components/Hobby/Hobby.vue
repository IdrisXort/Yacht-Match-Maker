<template>
  <div class="checkbox-container" :class="{'icon-active': status}">
    <p>{{hobby}}</p>
     <i :class="icon" @click="status=!status"></i>
    <input type="checkbox" :checked="status" @click="status=!status" name="hobby" :value="hobby" hidden>
  </div>
</template>
<script>
export default {
  props: ["hobby", "icon",'addHobby','deleteHobby'],
  data: function() {
    return {
      status: false
    };
  },
  watch: {
    status(doesntexist, exists) {
      if(doesntexist)this.addHobby(this.hobby);
      if(exists)this.deleteHobby(this.hobby);
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
  padding: 10px;
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
