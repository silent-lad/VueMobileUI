<template>
  <div
    class="multiButton"
    :class="[editing ? 'ribbon' : '', deleting ? 'delete' : '']"
  >
    <i v-if="deleting" class="fas fa-trash-alt"></i>
    <i v-else class="fas fa-plus"></i>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ribbonOn: false,
      trashZone: [],
      trashOptions: {
        group: {
          name: "trash",
          draggable: ".dropitem",
          put: () => true,
          pull: false
        }
      }
    };
  },
  props: ["editing", "deleting"]
};
</script>

<style>
.multiButton {
  position: fixed;
  bottom: 3%;
  right: 0;
  left: 0;
  margin: 0 auto;
  height: 12vh;
  width: 12vh;
  border-radius: 12vh;
  text-align: center;
  background: rgb(80, 124, 245);
  transition: all 0.3s linear;
  z-index: 5;
}
.multiButton > i {
  position: relative;
  font-size: 5vh;
  top: 29%;
  color: white;
}
.ribbon {
  border-radius: 0;
  width: 100%;
  bottom: 0;
  right: 0;
}
.delete {
  transform: scale(1.2);
  background: rgb(214, 55, 34);
}
</style>
