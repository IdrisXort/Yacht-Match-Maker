<template>
  <div class="introduction-Container">
    <p class="col-md-8">
      Met Match finder proberen wij achter te komen wat jij voor persoon je
      bent en wat je wilt in je volgende werkgever. Op die manier kunnen wij
      het bedrijf vinden dat het meest bij jouw behoefte past. Vul de
      antwoorden zo eerlijk mogelijk in, dan kunnen wij jou op de beste
      manier helpen.
    </p>
    <div class="introduction">
      <img class="introduction--image" src="../../assets/labirent.png">
      <br>
    </div>
  </div>
</template>
<script>
import B from "./../../Components/Buttons/Button";
import labirent from '../../assets/labirent.png';
export default {
  components: {
    Button: B,
    labirent:labirent
  },
  data() {
    return {};

  }
  
};
</script>
<style>
.introduction {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin: auto;
}
.introduction--image {
  width: 450;
}

</style>


