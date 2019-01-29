<template>
  <div class="BreadCrumb-container">
    <div class="BreadCrumb-relative">
      <div class="speech-container">
        <p class="speech" v-if="pageNumber<4 && isActive">
          <span>{{breadcrumbSpeechBubbles}}</span>
        </p>
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
  width: 35px;
  height: 35px;
  border-radius: 50%;
  font-size: 12px;
  line-height: 35px;
  text-align: center;
  margin: 10px 5px;
  background-color: #fff;
  color: #0f1941;
  cursor: pointer;
  border: 1px solid #0f1941;
}

.circle:hover {
  background-color: #0f1941;
  color: #fff;
  transition: 0.3s;
}

.circle--active {
  background-color: #0f1941;
  color: #fff;
  border: 1px solid #0f1941;
}

.breadcrumb__hr {
  height: 1px;
  width: 100px;
  margin: auto;
  background-color: #0f1941;
}

.breadcrumb__hr--active {
  height: 3px;
  transition: 0.2s;
  border-radius: 10px;
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
  font-size: 12px;
  width: 160px;
  padding: 12px;
  height: 55px;
  text-align: center;
  line-height: 15px;
  background-color: #0f1941;
  border-radius: 7px;
}

.speech::before {
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  left: 25px;
  top: 55px;
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
  top: -60px;
  left: 15px;
}
</style>