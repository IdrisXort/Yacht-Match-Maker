<template>
  <div class="container">
      <result 
      v-for="(result,index) in results.sort(function(res1,res2){return res1.totalMatch-res2.totalMatch}).reverse()"
      :key="index"
      :companyName="result.companyName"
      :matchPercentage="result.totalMatch+'%'"
      />
  </div>
</template>

<script>
import Result from "../../Components/Result/Result";
export default {
  components: {
    Result: Result
  },
  props:['results']
};
</script>

<style>
</style>
