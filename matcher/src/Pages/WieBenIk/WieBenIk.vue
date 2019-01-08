<template>
  <div>
    <br>
    <text-input-field whatToChange="name" label="What is je naam? "/>
    <br>
    <text-input-field
      whatToChange="selfInfo"
      label="Hoe zou je jezelf willen introduceren in één zin? "
    />
    <br>
    <image-input-field/>
    <br>
    <hobies/>
    <br>
  </div>
</template>
<script>
import TextInputField from "../../Components/TextInputField/TextInputField";
import ImageInputField from "./../../Components/ImageInputField/ImageInputField";
import Hobies from "../../Components/Hobies/Hobies";
export default {
  components: {
    TextInputField: TextInputField,
    ImageInputField: ImageInputField,
    Hobies: Hobies
  },
  data() {
    return {};
  }
};
</script>
