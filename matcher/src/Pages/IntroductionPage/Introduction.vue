<template>
  <div class="introduction-Container col-12">
    <label class="intro__Label">Welkom bij de Yacht match finder!</label>
    <p class="intro__text">
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
<style scoped>
.introduction {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin: auto;
}
.introduction--image {
  width: 500px;
}

.intro__text {
  font-size:20px;
  color:#57606f;
}

.intro__Label{
		font-size:20px;
	}
</style>


