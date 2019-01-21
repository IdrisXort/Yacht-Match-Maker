<template>
  <div>
    <h5>Nog even geduld...</h5>
    <p>Wij zijn hard bezig met jouw beste matches te vinden, een
    moment geduld alsjeblieft.</p>
    <b-progress :value="counter" :max="max" show-progress animated></b-progress>
    </div>
</template>

<script>
import {EventBus} from './../../Event-bus';
export default {
  data () {
    return {
      counter: 0,
      max: 100,
    }
  },
  props:['next'],
mounted(){
this.changeCounter();
},
  methods:{
      changeCounter(){      
          var id=   setInterval(()=>{
                 this.counter+=20;
             if(this.counter==100){
               clearInterval(id);
               this.next()
         
               }

             },1000);
         }  
  }
}
</script>
