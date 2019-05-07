<template>
  <div class="userPanel">
    <div class="userGreeting">
      <div class="heading">Hello SilentLad</div>
      <div class="taskSubHeading">You have 3 tasks</div>
    </div>

    <img class="userImage" src="@/assets/self.png" alt="" />
  </div>
</template>

<script>
export default {
  name: "userpanel"
};
</script>

<style>
.userPanel {
  height: 12vh;
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
  height: 8vh;
  width: 8vh;
  /* border: 1px solid black; */
  border-radius: 50%;
  margin: 1% 0%;
  box-shadow: 2px 2px 10px rgba(20, 20, 20, 0.2);
}
</style>
