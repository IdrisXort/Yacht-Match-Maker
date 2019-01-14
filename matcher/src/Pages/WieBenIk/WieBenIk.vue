<template>
  <div>
    <br>
    <text-input-field whatToChange="name" label="Wat is je naam? "/>
    <br>
    <text-input-field
      whatToChange="selfInfo"
      label="Hoe zou je jezelf willen introduceren in één zin? "
    />
    <br>
    <image-input-field label='Upload je foto, zodat wij een profiel voor je kunnen aanmaken.'/>
    <br>
    <hobbies label='Wat zijn je hobby’s?'/>
    <br>
  </div>
</template>
<script>
import TextInputField from "../../Components/TextInputField/TextInputField";
import ImageInputField from "./../../Components/ImageInputField/ImageInputField";
import Hobbies from "../../Components/Hobbies/Hobbies";
export default {
  components: {
    TextInputField: TextInputField,
    ImageInputField: ImageInputField,
    Hobbies: Hobbies
  },
  data() {
    return {};
  }
};
</script>
