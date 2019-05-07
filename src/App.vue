<template>
  <div id="app">
    <user-panel></user-panel>
    <div class="taskList">
      <task-panel></task-panel>
      <task-panel></task-panel>
      <task-panel></task-panel>
      <task-panel></task-panel>
    </div>
    <multi-button></multi-button>
  </div>
</template>

<script>
import UserPanel from "@/components/UserPanel.vue";
import TaskPanel from "@/components/TaskPanel.vue";
import MultiButton from "@/components/MultiButton.vue";

export default {
  name: "app",
  components: {
    UserPanel,
    TaskPanel,
    MultiButton
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Libre+Franklin");
body {
  font-family: "Libre Franklin", sans-serif;
  font-weight: 600;
}
</style>
