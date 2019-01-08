<template>
<input type="file"
       accept="image/png, image/jpeg"
       @change="getImage"
       >
</template>
<script>
import { EventBus } from '../../Event-bus';
export default {
    data(){
        return{
            image:null

        }
    },
  methods: {
      getImage(event){
          this.image=event.target.value;

          EventBus.$emit('imageTaken',this.image);
      }
  }
};
</script>
