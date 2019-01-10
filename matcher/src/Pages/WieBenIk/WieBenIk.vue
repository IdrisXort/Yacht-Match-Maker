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
    <hobies label='Wat zijn je hobby’s? (meerdere keuzes mogelijk)'/>
    <br>
    <CheckboxField />
  </div>
</template>
<script>
import TextInputField from "../../Components/TextInputField/TextInputField";
import ImageInputField from "./../../Components/ImageInputField/ImageInputField";
import Hobies from "../../Components/Hobies/Hobies";
import CheckboxField from "../../Components/CheckboxField/CheckboxField"
export default {
  components: {
    TextInputField: TextInputField,
    ImageInputField: ImageInputField,
    Hobies: Hobies,
    CheckboxField: CheckboxField,
  },
  data() {
    return {};
  }
};
</script>
