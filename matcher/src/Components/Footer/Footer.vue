<template class="footer">
    <nav class="navbar fixed-bottom navbar-light">
      <span class="copyright">© Yacht 2019 </span>
    </nav>
    <!-- Ⓒ -->
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
			/* -webkit-box-shadow: 0 -3px -20px 0 rgba(0,0,0,.1);
			-moz-box-shadow: 0 -3px -20px 0 rgba(0,0,0,.1);
			box-shadow: 0 -3px -20px 0 rgba(0,0,0,.1); */
			background-color:white;
			-webkit-box-shadow: 0px -5px 20px rgba(0, 0, 0, 0.1);
			-moz-box-shadow: 0px -5px 20px rgba(0, 0, 0, 0.1);
			box-shadow: 0px -5px 20px rgba(0, 50, 0, 0.1);
    }
    .copyright{
      font-family: Helvetica;
      color: #0f1941;
      font-weight: 700;
      font-size:12pt;
      padding:10px;
      display: flex;
      align-items: center;
      flex-direction: column;
			margin: auto;
    }
</style>