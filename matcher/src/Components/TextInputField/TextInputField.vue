<template>
  <input type="text" @change="changeName">
</template>
<script>
import { EventBus } from '../../Event-bus';
export default {
    data(){
        return{
            name:''
        }
    },
  methods: {
      changeName(event){
          this.name=event.target.value;
          EventBus.$emit('nameChanged',this.name);
      }
  }
};
</script>
