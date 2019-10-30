<template>
  <div class="editPanel">
    <i class="fas fa-times" @click="$emit('close')"></i>
    <textarea
      ref="text"
      class="editTask"
      v-model="text"
      placeholder="What Would you Like to Add?"
    ></textarea>
  </div>
</template>

<script>
export default {
  data() {
    return { text: "" };
  },
  watch: {
    text: function(newText, oldText) {
      this.$emit("typed", this.text);
    }
  },
  mounted() {
    setTimeout(() => {
      this.$refs.text.focus();
    }, 0);
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
  padding: 2%;
  font-size: 8vw;
}
.editTask:focus {
  border-style: none;
  border-color: Transparent;
  outline: none !important;
}
.editPanel > i {
  margin-bottom: 5%;
  text-shadow: 3px 3px 10px rgba(0, 0, 0, 0.397);
}
</style>
