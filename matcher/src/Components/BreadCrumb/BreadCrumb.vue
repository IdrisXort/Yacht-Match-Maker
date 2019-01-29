<template>
  <div class="BreadCrumb-container">
    <div class="BreadCrumb-relative">
      <div class="speech-container">
        <div class="speech" v-if="pageNumber<4 && isActive">
          <span>{{breadcrumbSpeechBubbles}}</span>
        </div>
      </div>
    </div>
    <div class="BreadCrumb-circle-hr-container" v-if="pageNumber<4">
      <div :class="{'circle--active': isActive}" class="circle">
        <i :class="breadcrumbIcons"></i>
      </div>
      <hr
        :class="{'breadcrumb__hr--active': isActive}"
        class="breadcrumb__hr"
        v-show="pageNumber<3"
      >
    </div>
  </div>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return (
      {
        pageNumber: 0
      },
      methods
    );
  },
  props: [
    "pageNumber",
    "isActive",
    "breadcrumbIcons",
    "breadcrumbSpeechBubbles"
  ]
};
</script>
<style>
.circle {
  width: 55px;
  height: 55px;
  border-radius: 50%;
  font-size: 22px;
  line-height: 50px;
  text-align: center;
  margin: 10px;
  background-color: #fff;
  color: #0f1941;
  cursor: pointer;
  border: 1px solid #0f1941;
  transition: 0.5s;
}

.circle:hover {
  background-color: #0f1941;
  color: #fff;
  transition: 0.5s;
}

.circle--active {
  background-color: #0f1941;
  color: #fff;
  border: 1px solid #0f1941;
}

.breadcrumb__hr {
  height: 1px;
  width: 300px;
  margin: auto;
  background-color: #0f1941;
}

.breadcrumb__hr--active {
  height: 3px;
  transition: 0.2s;
}

.BreadCrumb-circle-hr-container {
  display: inline-flex;
}

.box {
  position: relative;
  width: 200px;
  padding: 15px;
  margin: 1em 0 3em;
  color: #000;
  background: #f3961c;
  border-radius: 10px;
}

.box::after {
  content: "";
  position: absolute;
  bottom: -15px;
  left: 50px;
  border-width: 15px 15px 0;
  border-style: solid;
  border-color: #f3961c transparent;
  display: block;
  width: 0;
}

.speech {
  position: relative;
  color: #fff;
  font-size: 15px;
  width: 190px;
  padding: 12px;
  height: 65px;
  text-align: left;
  line-height: 19px;
  background-color: #0f1941;
  border-radius: 7px;
}

.speech::before {
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  left: 25px;
  top: 65px;
  border: 8px solid;
  border-color: #0f1941 transparent transparent #0f1941;
}

.BreadCrumb-container {
  display: inline-table;
}

.BreadCrumb-relative {
  position: relative;
}

.speech-container {
  position: absolute;
  top: -65px;
  left: 50px;
}
</style>