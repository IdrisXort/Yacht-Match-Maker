<template>
  <div>
      <br />
      <result 
      v-for="(result,index) in results.sort(function(res1,res2){return res2.totalMatch-res1.totalMatch})"
      :key="index"
      :companyName="result.companyName"
      :matchPercentage="result.totalMatch"
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
