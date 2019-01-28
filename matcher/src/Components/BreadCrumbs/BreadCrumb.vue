<template>
  <div class="BreadCrumb-container" v-if="pageNumber<4">
    <div :class="{'circle--active': isActive}" class="circle">{{pageNumber}}
    </div>
    <hr :class="{'breadcrumb__hr--active': isActive}" class="breadcrumb__hr" v-show="pageNumber<3">
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
  props: ["pageNumber", "isActive"]
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

.BreadCrumb-container {
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
</style>