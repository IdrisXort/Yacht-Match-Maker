<template>
    <div>
        dit is werk paginaa
        <Map/>
        <hard-skills :skills="skills" label="Kies je Hard Skills" />
    </div>
</template>
<script>
import Map from "../../Components/Map/Map";
import HardSkills from '../../Components/HardSkills/HardSkills';
export default {
    components: {
    Map: Map,
    HardSkills:HardSkills
    },
    data(){
        return{}
    },
    props:['skills']
}
</script>

