<template>
  <div class="task">
    <i class="clock far fa-clock"></i>
    <div class="taskText">
      <p class="taskHeading">{{ task.name }}</p>
      <p class="taskDueDate">Due Fri Aug 8</p>
    </div>
  </div>
</template>

<script>
export default { name: "taskpanel", props: ["task"] };
</script>

<style>
.task {
  /* height: 11vh; */
  margin: 4%;
  border-radius: 5px;
  box-shadow: 2px 2px 10px rgba(20, 20, 20, 0.2);
}
.taskHeading {
  font-size: 5vw;
  margin: 0;
}
.taskDueDate {
  font-size: 4vw;
  color: grey;
  margin: 3px 0;
}
.taskText {
  /* margin: 5%; */
  padding: 5% 4%;
}
.clock {
  float: right;
  padding: 6.5%;
  font-size: 3vw;
}
</style>
