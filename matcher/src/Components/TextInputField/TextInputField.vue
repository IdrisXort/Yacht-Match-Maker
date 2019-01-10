<template>
<div>
<Label class="label">{{label}}</Label>
  <input type="text" :whatToChange="whatToChange" @change="changeName" class="input__field">
</div>
</template>
<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      whatToChange: ""
    };
  },
  props: ["whatToChange",'label'],
  methods: {
    changeName(event) {
      if (this.whatToChange == "name") {
        EventBus.$emit("nameChanged", event.target.value);
      } else {
        EventBus.$emit("SelfInfoChanged", event.target.value);
      }
    }
  }
};
</script>
<style>
  .label{
    width: 100%;
    display: inline-block;
  }
 
  .input__field {
    color:black;
    border: 2px solid #192a56;
    border-radius:5px;
    width: 50%; /* moet nog bepaald worden watvoor width het krijgt en als het 50% is dat het op mobiel/tablet 100% is*/
    padding: 5px;
    margin-top: 10px;
    font-size: 14px;
    line-height: 20px;
    }

  .input__field:focus {
    border-color: #192a56;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(3, 5, 83, 0.6);

  }
</style>