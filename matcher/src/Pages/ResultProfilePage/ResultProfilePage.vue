<template>
  <div class="row">
    <div class="col-sm-8 profile-container">
      <div class="row">
        <div class="col-sm-4">
          <div class="profile--picture-container">
            <div class="profile--picture">
              <div class="profile--label">Profile picture</div>
            </div>
            <p>
              <b>
                Name:
              </b>
              <br>
              <span>{{ name }}</span>
            </p>
            <p>
              <b>
                Email address:
              </b>
              <br>
              <span>nog-geen@email.adres</span>
              </p>
          </div>
        </div>
        <div class="col-sm-8 profile--details-container">
          <p class="profile--oneliner">
            <b>{{oneliner}}</b>
            <!-- Ik ben een leergierig en harde werker die elke
            dag iets nieuws wil leren.-->
          </p>
          <div class="profile--leerstijl-container">
            <div class="row">
              <div class="col-sm-3">
                <b>Denker</b>
                <img src="../../assets/images/denker-icon.png" alt>
              </div>
              <div class="col-sm-9 no-padding-left profile--leerstijl-details">
                <p>
                  De kracht van de denker ligt in zijn analytische vermogen. Hij is gericht op informatie,
                  feiten en begrippen die nodig zijn om een onderwerp conceptueel te begrijpen.
                  Daarbij zoeken naar logische samenhang en een intellectuele uitdaging.
                </p>
              </div>
            </div>
          </div>
          <div class="profile--icons-container">
            <p>
              <b>Hobbies</b>
            </p>
            <div class="row">
              <div class="profile--icons col-sm-2" v-for="(hobby, index) in hobbies" :key="index">
                <i :class="setHobbyClassName(hobby)"></i>
                <p>{{hobby}}</p>
              </div>
            </div>
          </div>
          <div class="profile--hardskills-container">
            <p>
              <b>HardSkills</b>
            </p>
            <div class="row">
              <div class="profile--icons col-sm-2" v-for="(skill, index) in skills" :key="index">
                <i :class="setHardskillClassName(skill)"></i>
                <p>{{skill}}</p>
              </div>
            </div>
          </div>
          <div class="profile-companies-container"></div>
        </div>
      </div>
      <div class="match-label">
        <b>Op zoek naar type bedrijf:</b>
      </div>
      <div class="row">
        <Match
          v-for="(result,index) in results.sort(function(res1,res2){return res2.totalMatch-res1.totalMatch}).splice(0,3)"
          :key="index"
          :companyName="result.companyName"
          :matchPercentage="result.totalMatch"
        />
      </div>
    </div>
  </div>
</template>
<script>
import Match from "../../Components/Match/Match";
export default {
  props: ["hobbies", "setHobbyClassName", "skills", "setHardskillClassName", "name", "results", "oneliner"],
  components: {
    Match: Match,
  }
};
</script>
<style>
.profile-container {
  border: 1.5px solid #87a0e6;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 40px;
}
.profile--picture {
  margin-bottom: 20px;
  border: 1.5px solid #87a0e6;
  border-radius: 8px;
  height: 230px;
  background-image: url("../../assets/images/sample-image.png");
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

.profile--icons {
  text-align: center;
  display: inline-table;
}

.profile--icons i {
  position: relative;
  padding: 10px;
}

.profile--icons i::before {
  font-size: 30px;
}

.match-label {
  margin-bottom: 30px;
}
</style>
