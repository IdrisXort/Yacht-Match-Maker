<template>
    <div>
        dit is werk paginaa
        <Slider></Slider>
        <Map :locations="locations" label="In welke regio's zou je het liefst willen werken?"/>
        <hard-skills :skills="skills" label="Kies je Hard Skills" />
    </div>
</template>
<script>
import Map from "../../Components/Map/Map";
import HardSkills from '../../Components/HardSkills/HardSkills';
import Slider from '../../Components/Slider/Slider'
export default {
    components: {
    Map: Map,
    HardSkills:HardSkills,
    Slider: Slider
    },
    data(){
        return{}
    },
    props:['skills', 'locations']
}
</script>

