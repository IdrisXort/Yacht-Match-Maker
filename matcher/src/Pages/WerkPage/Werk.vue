<template>
    <div>
        <br />
        <Map :locations="locations" label="In welke regio's zou je het liefst willen werken?"/>
        <br />
        <Slider label="Geef aan op de schaal hoe groot het bedrijf is waar je het liefst werkt"/>
        <br />
        <hard-skills :skills="skills" label="Kies je Hard Skills" />
        <br />
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

