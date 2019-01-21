<template>
  <div>
    <h5>Loading Screen</h5>
    <b-progress :value="value" :max="max" show-progress animated></b-progress>
    </div>
</template>

<script>
export default {
  data () {
    return {
      counter: 45,
      max: 100
    }
  }
}
</script>
