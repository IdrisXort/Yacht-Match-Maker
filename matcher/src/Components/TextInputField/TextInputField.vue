<template>
<div>
<Label class="label">{{label}}</Label>
  <input type="text" :whatToChange="whatToChange" @change="changeName" class="form-control input__field">
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
    width: 100%; /* moet nog bepaald worden watvoor width het krijgt*/
    padding: 5px;
    margin-top: 10px;
    font-size: 14px;
    line-height: 20px;
    }

  .form-control:focus {
    border-color: #273c75;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(39, 60, 117,1.0);
  }
</style>