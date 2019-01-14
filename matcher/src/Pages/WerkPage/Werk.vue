<template>
    <div>
        dit is werk paginaa
        <Map label="In welke regio's zou je het liefst willen werken?"/>
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

