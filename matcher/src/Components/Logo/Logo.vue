<template>
      <nav class="navbar sticky-top navbar-light">
        <a class="navbar-brand">
            <span class="logo d-inline-block align-center">YACHT</span>
            <span class="sublogo d-inline-block align-center">Match finder</span>
        </a>
      </nav>
</template>
<script>
    export default {

    }
</script>
<style scoped>
    h1,
    h3 {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
    }

    /* .logo-container {
        cursor: pointer;
    } */

    .logo {
        font-family: Helvetica;
        font-size: 30pt;/* font-size: 35pt; */
        font-weight: 700;
        letter-spacing: 2px;
        margin-right: 10px;
    }

    .sublogo {
        font-family: Helvetica;
        font-size: 20pt;/* font-size: 23pt; */
        color: #0f1941;
    } 
    nav{
      margin-bottom:50px;
      -webkit-box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
      -moz-box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
      box-shadow: 0 3px 15px 0 rgba(0,0,0,.1);
    }
    nav:hover{
      cursor: pointer;
      -webkit-box-shadow: 0 4px 20px 0 rgba(0,0,0,.2);
      -moz-box-shadow: 0 4px 20px 0 rgba(0,0,0,.2);
      box-shadow: 0 4px 20px 0 rgba(0,0,0,.2);
    }
</style>