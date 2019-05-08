<template>
  <div id="app">
    <user-panel :taskCount="tasks.length" v-if="!editing"></user-panel>

    <div v-if="!editing" class="taskList">
      <transition-group name="list" tag="p">
        <task-panel
          v-touch:swipe="swipeHandler(task)"
          :key="task.name"
          v-for="task in tasks"
          :task="task"
        ></task-panel>
      </transition-group>
    </div>
    <edit-task-panel
      @typed="typed"
      @close="editing = false"
      v-else
    ></edit-task-panel>
    <multi-button
      ref="dropzone"
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
      newTask: "",
      origin: { x: 0, y: 0 }
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
    // movedHandler(e) {
    //   this.origin.x = e.touches.pageX;
    //   this.origin.y = e.touches.pageY;
    // },
    // endHandler() {},
    // movingHandler(e) {
    //   try {
    //     var c = e.target;
    //     var x = e.pageX - this.origin.x;
    //     var y = e.pageY - this.origin.y;
    //     // console.log(e.pageX, this.origin.x);

    //     var css =
    //       "z-index:9999;pointer-events: none; transform: scale(1.05, 1.05) rotateX(0deg) translate3d(" +
    //       x +
    //       "px, " +
    //       y +
    //       "px, 0px);";
    //     c.style.cssText = css;
    //   } catch (er) {
    //     console.log(er);
    //   }
    // },
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
</style>
