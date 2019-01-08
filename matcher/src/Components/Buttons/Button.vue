<template>
  <button class="btn" @click="onClick">{{text}}</button>
</template>
<script>
export default {
  props: ["onClick", "text"],
  data() {
    return {};
  }
};
</script>
