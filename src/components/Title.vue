<template>
  <div class="title">
    <img class="uk-flag" src="../assets/flag.jpg" alt="" />
    <h1>Digital Dashboard</h1>
  </div>
</template>

<script>
export default {
  name: "Title"
}
</script>

<style scoped>
.title {
  grid-column: 1 / 5;
  grid-row: 1/2;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
}

.title h1 {
  font-weight: 100;
  font-size: 5.8vh;
  letter-spacing: 0.2vw;
  font-family: "Kanit", sans-serif;
}

.title span {
  padding: 4vh;
  text-decoration-color: rgb(37, 36, 36);
}

.uk-flag {
  width: 3.5vw;
  height: 5vh;
  border-radius: 50%;
}

</style>