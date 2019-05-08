<template>
  <div id="app">
    <user-panel v-if="!editing"></user-panel>
    <div v-if="!editing" class="taskList">
      <task-panel
        :key="task.name"
        v-for="task in tasks"
        :task="task"
      ></task-panel>
    </div>
    <edit-task-panel
      @typed="typed"
      @close="editing = false"
      v-else
    ></edit-task-panel>
    <multi-button
      :editing="editing"
      v-touch:tap="handleMultiTap"
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
      editing: false,
      tasks: [],
      newTask: ""
    };
  },
  methods: {
    handleMultiTap() {
      if (this.editing) {
        this.tasks.push({ name: this.newTask });
        this.editing = false;
      } else {
        this.editing = true;
      }
    },
    typed(e) {
      this.newTask = e;
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Libre+Franklin");
body {
  font-family: "Libre Franklin", sans-serif;
  font-weight: 600;
  max-width: 1200px;
  margin: 0 auto;
}
</style>
