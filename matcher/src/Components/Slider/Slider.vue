<template>
  <div class="container">
    <div class="col-sm-8">
      <div class="row justify-content-between">
        <div class="col-2 slider-icon-container">
          <div class="icon-container" @click="numberRange = 50">
            <img src="../../assets/svg/klein.svg" class="icon-company">
            <p>
              Klein
              <span><50 mensen</span>
            </p>
          </div>
        </div>
        <div class="col-2 slider-icon-container">
          <div class="icon-container" @click="numberRange = 250">
            <img src="../../assets/svg/middel.svg" class="icon-company">
            <p>
              Middel
              <span><250 mensen</span>
            </p>
          </div>
        </div>
        <div class="col-2 slider-icon-container">
          <div class="icon-container" @click="numberRange = 400">
            <img src="../../assets/svg/multinational.svg" class="icon-company">
            <p>
              Multinational
              <span>>250 mensen</span>
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
        @change="getInfo()"
      >
      <p>{{ statusRange }}</p>
      <p>{{numberRange}}</p>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      statusRange: "Kies een branch",
      numberRange: ""
    };
  },
  methods: {
    getInfo() {
      var info = this.numberRange;
      // switch (info) {
      //   case info >250:
      //     this.statusRange = "Multinational";
      //     break;
      //   case info >51 || info <250:
      //     this.statusRange = "Middel";
      //     break;
      //   case info <0:
      //     this.statusRange = "Klein";
      //     break;
      //   default:
      //     this.statusRange = "Kies een branch";
      // }
      if (info > 250) {
        return this.statusRange = "Multinational";
      } else if (info > 51) {
        return this.statusRange = "Middel";
      } else if (info > 0) {
        return this.statusRange = "klein";
      }
    }
  },
};
</script>

<style>

/* Mijn tevergeefse pogingen om een font in the laden... */
/* @font-face {
  font-family: "matcherfont";
  /* src: url("../../assets/fonts/icomoon.eot") format('eot'); */
/* src: url("../../assets/fonts/icsomoon.svg") format('svg'); */
/* src: url("../../assets/fonts/icomoon.ttf") format('ttf'); */
/* src: url("../../assets/fonts/icomoon.woff") format('woff'); */
/* } */

/* body {
  font-family: 'matcherfont';
} */

.slider {
  -webkit-appearance: none;
  width: 100%;
  background: #4e4d8b;
  /* outline: none; */
  height: 3px;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 10px;
  height: 25px;
  background: #0f1941;
  border-radius: 3px;
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
  margin-bottom: 0px;
}

.icon-container span {
  display: block;
  font-size: 13px;
}
</style>
