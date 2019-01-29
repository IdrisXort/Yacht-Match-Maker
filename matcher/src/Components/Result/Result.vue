<template>
  <!-- tried with table -->
  <!-- <tr>
      <td>{{companyName}}</td>
      <td>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</td>
      <td @click="isShown = !isShown" colspan="2">lees meer</td>
      <td v-if="isShown">lala text</td>
    </tr> -->
    <div>
      <div class="row hover__table" @click="isShown = !isShown" :class="{ result__selection: isShown }">
        <div class="col-6">
          <p>{{companyName}}</p>
        </div>
        <div class="col-6 hover__table--result">
          <p>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</p>
        </div>
        <!-- <div class="col-4">
          <p>{{sector}}</p>
        </div>  -->
      </div>
      <div class="row result">
        <div class="col-12" :class="{ result: isShown }">
          <table class="table" v-if="isShown">{{ resultaat }}
            <thead>
              <tr>
                <th>Branche/sector</th>
                <th>Locatie</th>
                <th>Omvang</th>
                <th>Hardskills</th>
                <th>Softskills</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>{{ sector }}</td>
                <td>{{ location }}</td>
                <td>{{ capacity }}</td>
                <td>{{ hardskills }}</td>
                <td>{{ softskills }}</td>
              </tr>
            </tbody>
          </table>
        </div>
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
  props: ["companyName", "sector", "location", "capacity", "hardskills", "softskills", "matchPercentage"]
};
</script>

<style scoped>
  .result {
    background-color:#ecf0f1;
    -webkit-box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
    -moz-box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
    box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
  }

  .result__selection {
    font-weight: 700;
    background-color:#ecf0f1;
    -webkit-box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
    -moz-box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
    box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
  }
  .hover__table {
    padding-top:10px;
    cursor:pointer;
  }
  .hover__table:hover{
    background-color: #ecf0f1;
  }
  .hover__table--result{
    text-align:center;
  }

  th{
    font-weight:200;
  }
</style>
