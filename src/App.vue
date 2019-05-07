<template>
  <div id="app">
    <user-panel v-if="!editing"></user-panel>
    <div v-if="!editing" class="taskList">
      <task-panel></task-panel>
      <task-panel></task-panel>
      <task-panel></task-panel>
      <task-panel></task-panel>
    </div>
    <edit-task-panel @close="editing = false" v-else></edit-task-panel>
    <multi-button
      :editing="editing"
      v-touch:tap="
        () => {
          editing = !editing;
        }
      "
    ></multi-button>
  </div>
</template>

<script>
import UserPanel from "@/components/UserPanel.vue";
import TaskPanel from "@/components/TaskPanel.vue";
import MultiButton from "@/components/MultiButton.vue";
import EditTaskPanel from "@/components/EditTaskPanel.vue";

export default {
  name: "app",
  components: {
    UserPanel,
    TaskPanel,
    MultiButton,
    EditTaskPanel
  },
  data() {
    return {
      editing: false
    };
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
