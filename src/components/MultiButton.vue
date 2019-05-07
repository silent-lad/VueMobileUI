<template>
  <draggable
    v-model="trashZone"
    class="dropzone trashzone"
    :options="trashOptions"
  >
    <div
      @click="
        if (editing) {
          $emit('close');
        }
      "
      class="multiButton"
      :class="editing ? 'ribbon' : ''"
    >
      <i v-if="deleting" class="fas fa-trash-alt"></i>
      <i v-else class="fas fa-plus"></i>
    </div>
  </draggable>
</template>

<script>
import draggable from "vuedraggable";
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
  props: ["editing"],
  components: {
    draggable
  }
};
</script>

<style>
.multiButton {
  position: fixed;
  bottom: 3%;
  right: 0;
  left: 0;
  margin: 0 auto;
  /* left: auto; */
  /* margin: 0 auto; */
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
