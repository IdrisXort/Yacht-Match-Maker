<template>
  <!-- <div>
    <h2>{{companyName}}</h2>

    <h2>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</h2>
  </div> -->
  <!-- tried with table -->
  <!-- <tr>
      <td>{{companyName}}</td>
      <td>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</td>
      <td @click="isShown = !isShown" colspan="2">lees meer</td>
      <td v-if="isShown">lala text</td>
    </tr> -->
    <div class="row hover__table" @click="isShown = !isShown">
      <div class="col-3">
        <p>{{companyName}}</p>
      </div>
      <div class="col-3">
        <p>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</p>
      </div>
      <div class="col-3">
        <p>lees meer</p>
      </div>
      <div class="col-3" :class="{ result: isShown }">
        <p v-if="isShown">{{ resultaat }}</p>
      </div>
    </div>
</template>

<script>
export default {
   data () {
     return {
      isShown: false
    }
  },
  props: ["companyName", "matchPercentage"]
};
</script>

<style scoped>
  .result{
    background-color:orange;
    border-radius:10px;
    height:100px;
  }

  .hover__table {
    padding-top:10px;
    cursor:pointer;
  }
  .hover__table:hover{
    background-color: #ecf0f1;
  }
</style>
