<template>
  <button :class="className" @click="onClick">
    <i v-show="previousIcon" class="fas fa-caret-left icon__left"></i>
    {{text}}
    <i v-show="nextIcon" class="fas fa-caret-right icon__right"></i>
  </button>
</template>
<script>
export default {
  props: ["onClick", "text"],
  data() {
    return {
      className:'btn button__'+this.text,
      previousIcon:this.text == 'previous',
      nextIcon:this.text == 'next',
    };
  }
};
</script>
<style scoped>
  .btn {
    color:white;
    border:none;
    border-radius:6px;
    padding: 10px 20px;
    font-size: 16px;
    font-weight: 700;
    line-height: 25px;
    background-color: #192a56;
  } 

  .btn:focus {
    border-color: #273c75;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(39, 60, 117,1.0);
  }

  .btn:hover {
   /* we zien wel wat de hover wordt voor nu even iets subtiel*/
    border-color: #273c75;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(39, 60, 117,1.0);
  }

  .button__start {
    background-color: #e84118;
  }

  .icon__right {
    font-size: 14px;
    margin-left: .5em;
  }

  .icon__left{
    font-size: 14px;
    margin-right: .5em;
  }

</style>