<template>
    <progress-bar :next="next"></progress-bar>
</template>

<script>
import ProgressBar from "../../Components/ProgressBar/ProgressBar";
export default {
    components: {
        ProgressBar: ProgressBar
    },
    props:['next']
}
</script>
>
>

// import Hobbies from "../../Components/Hobbies/Hobbies";
// export default {
//   components: {
//     TextInputField: TextInputField,
//     ImageInputField: ImageInputField,
//     Hobbies: Hobbies
//   },
//   data() {
//     return {};
//   },
//   props:['hobbies', 'icons']
// };