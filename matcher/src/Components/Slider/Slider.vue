<template>
  <!-- <div class="col-sm-7">
        <div class="company-container">
                <div class="icon-company-container">
                    <img src="../../assets/svg/klein.svg" alt="">
                </div>
                <div class="icon-company-container">
                    <img src="../../assets/svg/middel.svg" alt="">

                </div>
                <div class="icon-company-container">
                    <img src="../../assets/svg/multinational.svg" alt="">

                </div>
        </div>
        <input type="range" min="1" max="3" value="50" class="slider">
  </div>-->
  <div class="container">
    <div class="col-sm-7">
      <div class="row justify-content-between">
        <div class="col-1">
          <!-- <img src="../../assets/svg/klein.svg" class="icon-company" alt> -->
          <object data="your.svg" type="image/svg+xml">
            <img src="../../assets/svg/klein.svg" class="icon-company" alt>
          </object>
        </div>
        <div class="col-1">
          <!-- <object id="svg1" data="../../assets/svg/middel.svg" type="image/svg+xml"></object> -->
          <!-- <img src="../../assets/svg/middel.svg" class="icon-company" alt> -->
          <!-- <img src="logo.png" srcset="../../assets/svg/middel.svg" alt="My logo"> -->
          <!-- <div class="test"></div> -->
          <object data="your.svg" type="image/svg+xml">
            <img src="../../assets/svg/middel.svg" class="icon-company" alt>
          </object>
        </div>
        <div class="col-1">
          <img src="../../assets/svg/multinational.svg" class="icon-company" alt>
          <!-- <span class="icon-klein" aria-hidden="true"></span> -->
        </div>
      </div>
      <input type="range" name="foo" min="1" max="3" value="50" class="slider" onchange="getInfo()">
      <p>
        {{ rangeStatus }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data: function(){
    return {
      rangeStatus: 'Kies een branch'
    }
  },
  methods: {
    getInfo(value){
      console.log(value).value;
    }
  }
};
</script>

<style>

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
}

.test::before {
    background: url("../../assets/svg/klein.svg");
    width: 50px;
    height: 50px;
    color: pink;
}
</style>
