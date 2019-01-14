<template>
  <tr>
    <th scope="col" >{{index}}.</th>
    <td><Label class="label">{{question}}</Label></td>
    <td><input class="input__radio" type="radio" v-model="selectedOption" @click="getSkill" :value="option1"></td>
    <td><input class="input__radio" type="radio" v-model="selectedOption" @click="getSkill" :value="option2"></td>
  </tr>
</template>

<script>
import { EventBus } from "../../Event-bus";
export default {
  data() {
    return {
      selectedOption: null,
      index: this.index,
    };
  },
  props: ["question", "option1", "option2", "getOption", "index"],
  methods: {
    getSkill: function(event) {
      if (event.target.checked) {
        this.selectedOption = event.target.value;
        this.getOption(this.index, this.selectedOption);
      }
    }
  }
};
</script>

<style scoped>
  .input__radio {
    min-width: 100px;
  }
  .label{
    font-size: 16px;
  }
</style>
