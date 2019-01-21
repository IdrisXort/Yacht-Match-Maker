<template>
  <!-- <div>
    <h2>{{companyName}}</h2>

    <h2>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</h2>
  </div> -->
    <div class="row">
      <div class="col-sm-6">
        <p class="result">{{companyName}}</p>
      </div>
      <div class="col-sm-6">
        <p class="result">{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</p>
      </div>
    </div>
</template>

<script>
export default {
  props: ["companyName", "matchPercentage"]
};
</script>

<style scoped>
  .result{
    font-size:20px;
  }
</style>
