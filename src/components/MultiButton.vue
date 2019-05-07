<template>
  <div class="multiButton">
    <i class="fas fa-plus"></i>
  </div>
</template>

<script>
export default {};
</script>

<style>
.multiButton {
  position: fixed;
  bottom: 3%;
  right: 40%;
  left: auto;
  /* margin: 0 auto; */
  height: 12vh;
  width: 12vh;
  border-radius: 12vh;
  text-align: center;
  background: rgb(80, 124, 245);
}
.multiButton > i {
  position: relative;
  font-size: 5vh;
  top: 29%;
  color: white;
}
</style>
