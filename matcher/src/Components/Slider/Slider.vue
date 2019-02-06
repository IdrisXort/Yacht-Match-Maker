<template>
  <div>
    <label>{{label}}</label>
    <div class="container no-padding-left">
      <div class="col-sm-8 no-padding-left">
        <div class="row justify-content-between">
          <div class="col-2 slider-icon-container">
            <div class="icon-container" @click="setRangeValueOnClick(50, 'Klein')">
              <img src="../../assets/svg/klein.svg" class="icon-company">
              <p>
                Klein
                <span>Minder dan 50 mensen</span>
              </p>
            </div>
          </div>
          <div class="col-2 slider-icon-container">
            <div class="icon-container" @click="setRangeValueOnClick(250, 'Middel')">
              <img src="../../assets/svg/middel.svg" class="icon-company">
              <p>
                Middel
                <span>Minder dan 250 mensen</span>
              </p>
            </div>
          </div>
          <div class="col-2 slider-icon-container">
            <div class="icon-container" @click="setRangeValueOnClick(450, 'Multinational')">
              <img src="../../assets/svg/multinational.svg" class="icon-company">
              <p>
                Multinational
                <span>Meer dan 250 mensen</span>
              </p>
            </div>
          </div>
        </div>
        <input
          type="range"
          name="foo"
          step="1"
          min="1"
          max="500"
          class="slider"
          v-model="numberRange"
          @change="getRangeValue()"
        >
        <p>{{ statusRange }}</p>
        <p>
          {{numberRange}}
          <span v-if="labelRange">mensen</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import { EventBus } from "./../../Event-bus";
export default {
  data: function() {
    return {
      statusRange: "Kies een branch",
      numberRange: "",
      labelRange: false
    };
  },
  props: ["label"],
  updated() {
    EventBus.$emit("capacityChanged", this.statusRange);
  },
  methods: {
    getRangeValue() {
      var info = this.numberRange;
      this.labelRange = true;
      if (info > 250) {
        return (this.statusRange = "Multinational");
      } else if (info > 51) {
        return (this.statusRange = "Middel");
      } else if (info > 0) {
        return (this.statusRange = "klein");
      }
    },
    setRangeValueOnClick(rangeValue, company) {
      this.labelRange = true;
      this.statusRange = company;
      this.numberRange = rangeValue;
    }
  }
};
</script>

<style>
.slider {
  -webkit-appearance: none;
  width: 100%;
  background: #4e4d8b;
  height: 3px;
  transition: 3s;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 10px;
  height: 25px;
  background: #0f1941;
  border-radius: 3px;
}

.slider::-webkit-slider-thumb:hover {
  background: #4e4d8b;
  transition: 0.3s;
}

.icon-company {
  vertical-align: bottom;
  width: 30px;
}

.test::before {
  background: url("../../assets/svg/klein.svg");
  width: 50px;
  height: 50px;
  color: pink;
}

.slider-icon-container {
  margin-top: 130px;
  position: relative;
  cursor: pointer;
}

.icon-container {
  position: absolute;
  margin-top: 150px;
  bottom: 0px;
  text-align: center;
}

.icon-container p {
  margin-top: 10px;
  margin-bottom: 0px;
}

.icon-container span {
  display: block;
  font-size: 13px;
}
</style>
