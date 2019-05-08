<template>
  <div id="app" :class="blur ? 'blur' : ''">
    <user-panel :taskCount="tasks.length" v-if="!editing"></user-panel>

    <div v-if="!editing" class="taskList">
      <draggable
        v-model="tasks"
        @start="deleting = true"
        @end="deleting = false"
        ghost-class="ghost"
      >
        <task-panel
          class="dropitem"
          :key="task.name"
          v-for="task in tasks"
          :task="task"
        ></task-panel>
        <!-- </transition-group> -->
      </draggable>
    </div>
    <edit-task-panel
      @typed="typed"
      @close="editing = false"
      v-else
    ></edit-task-panel>
    <draggable :options="trashOptions">
      <multi-button
        :editing="editing"
        :deleting="deleting"
        v-touch:tap="handleMultiTap"
      ></multi-button>
    </draggable>
  </div>
</template>

<script>
import UserPanel from "@/components/UserPanel.vue";
import TaskPanel from "@/components/TaskPanel.vue";
import MultiButton from "@/components/MultiButton.vue";
import EditTaskPanel from "@/components/EditTaskPanel.vue";
import draggable from "vuedraggable";

export default {
  name: "app",
  components: {
    UserPanel,
    TaskPanel,
    MultiButton,
    EditTaskPanel,
    draggable
  },
  data() {
    return {
      blur: false,
      editing: false,
      tasks: [],
      newTask: "",
      deleting: false,
      origin: { x: 0, y: 0 },
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
  methods: {
    handleMultiTap() {
      if (this.editing) {
        if (this.newTask) {
          this.tasks.push({ name: this.newTask });
          this.editing = false;
        }
      } else {
        this.editing = true;
        this.newTask = "";
      }
    },
    swipeHandler(task) {
      return (direction, event) => {
        console.log(direction, task);
        if (direction == "right") {
          this.tasks.splice(this.tasks.indexOf(task), 1);
        }
      };
    },
    typed(e) {
      this.newTask = e;
    }
  },
  watch: {
    deleting(latest, Old) {
      if (latest) {
        this.blur = true;
      } else {
        this.blur = false;
      }
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
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  background: rgb(146, 40, 40);
  transform: translateX(100px);
}
.ghost {
  opacity: 0.5;
  color: grey;
  /* transform: scale(1.2); */
}
</style>
