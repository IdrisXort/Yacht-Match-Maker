<template>
  <div>
      <br>
    <text-input-field/><br>
    <image-input-field/><br>
    <hobies/><br>
  </div>
</template>
<script>
import TextInputField from "../../Components/TextInputField/TextInputField";
import ImageInputField from "./../../Components/ImageInputField/ImageInputField";
import  Hobies  from "../../Components/Hobies/Hobies";
export default {
  components: {
    TextInputField: TextInputField,
    ImageInputField: ImageInputField,
    Hobies:Hobies
  },
  data() {
    return {
    };
  }
};
</script>
