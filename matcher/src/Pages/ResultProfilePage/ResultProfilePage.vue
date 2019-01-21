<template>
  <div class="row">
    <div class="col-sm-8 profile-container">
      <div class="row">
        <div class="col-sm-4">
          <div class="profile--picture-container">
            <div class="profile--picture">
              <div class="profile--label">Profile picture</div>
            </div>
            <p>Name:</p>
            <p>Emailadres:</p>
          </div>
        </div>
        <div class="col-sm-8 profile--details-container">
          <p class="profile--oneliner">
            Ik ben een leergierig en harde werker die elke
            dag iets nieuws wil leren.
          </p>
          <div class="profile--leerstijl-container">
            <div class="row">
              <div class="col-sm-3">
                <b>Denker</b>
                <img src="../../assets/images/denker-icon.png" alt>
              </div>
              <div class="col-sm-9 no-padding-left profile--leerstijl-details">
                <p>
                  De kacht van de denker ligt in zijn analytische vermogen. Hij is gericht op informatie,
                  feiten en begrippen die nodig zijn om een onderwerp conceptueel te begrijpen.
                  Daarbij zoeken naar logische samenhang en een intellectuele uitdaging.
                </p>
              </div>
            </div>
          </div>
          <div class="profile--hobbies-container">
            <b>Hobbies</b>
          </div>
          <div class="profile-companies-container"></div>
        </div>
      </div>
      <p>
        <b>Op zoek naar type bedrijf:</b>
      </p>
      <div class="row">
        <Match/>
        <Match/>
        <Match/>
      </div>
    </div>
  </div>
</template>
<script>
import Match from "../../Components/Match/Match";
export default {
  components: {
    Match: Match
  }
};
</script>
<style>
.profile--picture-container {
  /* margin: 10px; */
}

.profile-container {
  border: 1.5px solid #87a0e6;
  border-radius: 8px;
  padding: 20px;
}
.profile--picture {
  margin-bottom: 20px;
  border: 1.5px solid #87a0e6;
  border-radius: 8px;
  height: 230px;
  background-image: url("../../assets/images/sample-image.jpg");
  background-position: center;
  background-size: cover;
}

.profile--label {
  background-color: #325d835e;
  color: white;
  position: relative;
  top: 75%;
  transform: translateY(-50%);
  text-align: center;
}

.profile--details-container {
  /* padding: 10px; */
  
}

.profile--leerstijl-container {
    margin-bottom: 20px;

}

.profile--leerstijl-details {
  position: relative;
}

.profile--leerstijl-details p {
  position: absolute;
  bottom: 0px;
  font-size: 12px;
  margin-bottom: 0px;
  width: 90%;
}
</style>
