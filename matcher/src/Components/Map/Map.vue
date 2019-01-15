<template>
  <div>
    <label>{{label}}</label>
    <div class="dropdown">
      <!-- idee voor als we een map gaan gebruiken <img id="Image-Maps-Com-image-maps-2019-01-14-024229" src="http://www.image-maps.com/m/private/0/p6qahjsb45e67i40mj6a25kij5_nederland.png" border="0" width="504" height="597" orgWidth="504" orgHeight="597" usemap="#image-maps-2019-01-14-024229" alt="" />
      <map name="image-maps-2019-01-14-024229" id="ImageMapsCom-image-maps-2019-01-14-024229">
          <area  alt="" title="" href="http://www.image-maps.com/" shape="rect" coords="167,206,217,256" style="outline:none;" target="_self"     />
          <area shape="rect" coords="502,595,504,597" alt="Image Map" style="outline:none;" title="Image Map" href="http://www.image-maps.com/index.php?aff=mapped_users_0" />
          <area  alt="" title="" href="http://www.image-maps.com/" shape="poly" coords="0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0" style="outline:none;" target="_self"     />
          <area  alt="" title="" href="http://www.image-maps.com/" shape="poly" coords="0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0" style="outline:none;" target="_self"     />
          <area  alt="" title="" href="http://www.image-maps.com/" shape="poly" coords="147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332,147,332" style="outline:none;" target="_self"     />
      </map>-->
      <Button
        v-html="text"
        class="dropdown-toggle button__dropdown"
        type="button"
        id="chooseLocationButton"
        data-toggle="dropdown"
        aria-haspopup="true"
        aria-expanded="false"
      />
      <div class="dropdown-menu" aria-labelledby="chooseLocationButton">
        <a
          class="dropdown-item"
          href="#"
          v-for="(location,index) in locations"
          :key="index"
          @click="setLocation(index)"
        >{{location}}</a>
      </div>
    </div>
  </div>
</template>
<script>
import Button from "../Buttons/Button";
import { EventBus } from "../../Event-bus";
export default {
  components: {
    Button: Button
  },
  props: ["label", "locations"],
  data() {
    return {
      text: "kies je regio",
      chosenLocation: ""
    };
  },
  methods: {
    setLocation(index) {
      EventBus.$emit("ChooseLocation", this.locations[index]);
      this.text=this.locations[index];
      console.log(this.locations[index]);
    }
  }
};
</script>
