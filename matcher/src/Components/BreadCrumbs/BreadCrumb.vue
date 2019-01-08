<template>
  <div class="BreadCrumb-container">
    <button class="circle"> <span  >1</span></button><hr>
    <button class="circle"> <span  >2</span></button><hr>
    <button class="circle"> <span  >3</span></button><hr>
    <button class="circle"> <span  >4</span></button><hr>
    <button class="circle"> <span  >5</span></button>

  </div>
</template>

<script>
export default {
  data() {
    return;
  }
};
</script>
<style>
.circle{
    display: flex;
    align-items: center;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    text-align: center;
    margin: auto;
}
hr{
    width: 100px;
}
.BreadCrumb-container{

    display: flex;
    align-items: center;
}

</style>

