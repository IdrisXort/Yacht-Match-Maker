<template>
  <div class="BreadCrumb-container">
    <button class="circle">{{pageNumber}}</button>
    <hr>
  </div>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      pageNumber: 0
    };
  },
  props: ["pageNumber"]
};
</script>
<style>
.circle {
  display: flex;
  align-items: center;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  text-align: center;
  margin: auto;
}
hr {
  width: 100px;
}
.BreadCrumb-container {
  display: flex;
  align-items: center;
}
</style>

