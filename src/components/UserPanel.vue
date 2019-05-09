<template>
  <div class="userPanel">
    <div class="userGreeting">
      <div class="heading">Hello SilentLad</div>
      <div class="taskSubHeading">
        You have {{ taskCount }} tasks <br />
        Drag to delete or reorder.
      </div>
    </div>
    <img class="userImage" src="@/assets/self.png" alt="" />
  </div>
</template>

<script>
export default {
  name: "userpanel",
  props: ["taskCount"]
};
</script>

<style>
.userPanel {
  height: 22vw;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 10% 5% 0% 5%;
}
.taskSubHeading {
  font-weight: lighter;
  color: darkgrey;
  font-size: 5vw;
}
.heading {
  font-weight: bold;
  color: black;
  font-size: 8vw;
}
.userImage {
  height: 14vw;
  width: 14vw;
  border-radius: 50%;
  margin: 1% 0%;
  box-shadow: 2px 2px 10px rgba(20, 20, 20, 0.2);
}
</style>
