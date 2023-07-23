<template>
  <div class="presente">
    <div class="fita-1"></div>
    <div class="fita-2"></div>
    <div class="topo"></div>
    <div class="corpo"></div>
  </div>
</template>

<script>
export default {
name: 'Presente'
}
</script>

<style>
.presente {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 10;
}
.topo {
    width: 100px;
    height: 25px;
    background-color: #7aa944;
}
.corpo {
    width: 90px;
    height: 60px;
    background-color: #5c7e32;
}
.fita-1 {
    position: absolute;
    width: 15px;
    height: 85px;
    background-color: red;
}
.fita-2 {
    position: absolute;
    top: 40px;
    width: 90px;
    height: 15px;
    background-color: red;
}
</style>