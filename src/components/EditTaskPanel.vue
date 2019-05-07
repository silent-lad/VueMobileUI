<template>
  <div class="editPanel">
    <i class="fas fa-times" @click="$emit('close')"></i>
    <textarea
      class="editTask"
      v-model="text"
      placeholder="What Would you Like to Add?"
    >
dfz</textarea
    >
  </div>
</template>

<script>
export default {
  data() {
    return { text: "" };
  }
};
</script>

<style>
.editTask {
  height: 80vh;
  width: 100%;
  /* border: 1px solid grey; */
  border-style: none;
  border-color: Transparent;
  overflow: auto;
  font-size: 8vw;
  font-family: "Libre Franklin", sans-serif;
}
.editPanel {
  font-size: 8vw;
}
.editTask:focus {
  border-style: none;
  border-color: Transparent;
  outline: none !important;
}
.editPanel > i {
  text-shadow: 3px 3px 10px rgba(0, 0, 0, 0.397);
}
</style>
