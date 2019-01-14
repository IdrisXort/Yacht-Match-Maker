<template>
  <div>
    <p>
      <Label>{{label}}</Label>(meerdere keuzes mogelijk)
    </p>
    <br>
    <input type="checkbox" @click="getHobby" name="hobby" value="sporten">
    <label for="hobby">sporten</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="muziek">
    <label for="hobby">muziek</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="fotograferen">
    <label for="hobby">fotograferen</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="koken">
    <br>
    <label for="hobby">koken</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="tekenen">
    <label for="hobby">tekenen</label>
    <input type="checkbox" @click="getHobby" name="hobby" value="lezen">
    <label for="hobby">lezen</label>
    <div class="row">
      <div class="container">
        <div class="col-sm-7">
          <div class="row">
            <div class="col-sm">
              <div
                class="checkbox-container"
                :class="{'icon-active': iconActive}"
                value="sport"
              >
                <i class="fas fa-running"></i>
                <br>
                <p>Sporten</p>
                <input type="checkbox" @click="getHobby" name="hobby" value="Sporten">
              </div>
            </div>
            <div class="col-sm">
              <div
                class="checkbox-container"
                :class="{'icon-active': iconActive}"
                value="muziek"
              >
                <i class="fas fa-music"></i>
                <br>
                <p>Muziek</p>
                <input type="checkbox" @click="getHobby" name="hobby" value="Muziek">
              </div>
            </div>
            <div class="col-sm">
              <div
                class="checkbox-container"
                :class="{'icon-active': iconActive}"
                value="fotograferen"
              >
                <i class="fas fa-camera-retro"></i>
                <br>
                <p>Fotograferen</p>
                <input type="checkbox" @click="getHobby" name="hobby" value="Fotograferen">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      hobbies: [],
      iconActive: false
    };
  },
  props: ["label"],
  methods: {
    getHobby(event) {
      this.iconActive = !this.iconActive;
      if (event.target.checked) {
        this.hobbies.push(event.target.value);
      } else {
        this.hobbies = this.hobbies.filter(a => a != event.target.value);
      }
      EventBus.$emit("hobyChanged", this.hobbies);
    },
    getHobby2() {
      this.iconActive = !this.iconActive;
      // return 'icon-active';

      // console.log(event.target.attributes['value'].value);
      // console.log(event);
    }  
  }
};
</script>

<style>
.checkbox-container {
  padding: 15px;
  border-radius: 15px;
  text-align: center;
}

.checkbox-container i {
  position: relative;
}
.checkbox-container i::before {
  font-size: 100px;
  /* position:absolute; */
  /* top:45%; */
  /* left:45%; */
}

.checkbox-container span {
  text-align: center;
}

.checkbox-container p {
  text-align: center;
}

.checkbox--icon {
  display: inline;
}

.icon-active {
  color: white;
  background: #0f1941;
  transition: 1s;
}

.icon-active p {
  color: white;
  transition: 1s;
}
</style>