<template>
  <div class="room-uses">
    <div class='room-uses-grid-container'>
      <div class='room-uses-grid'>
        <div class='room-uses-title'>Room Uses</div>
        <div class='room-uses-data-container1'>
          <ul style="margin-left: 1vw">
            <li>IT 1:</li>
            <p style="display:block">Class: 10C</p>
            <li>IT 2:</li>
            <p>Class: 10C</p>
          </ul>
        </div>
        <div class='room-uses-data-container2'>
          <ul>
            <li>IT 1:</li>
            <p style="display:block">Class: 10C</p>
            <li>IT 2:</li>
            <p>Class: 10C</p>
          </ul>
        </div>

        <div class='room-line1'>
          <div>

          </div>
        </div>
        <div class='room-line2'>
          <div>

          </div>
        </div>
        <div class='logo'>
          <img src="../assets/logo.png" width="2" height="5" alt="">
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "Room-uses"
}
</script>

<style scoped>
.room-uses {
  grid-column: 5/7;
  grid-row: 3/8;
}

.room-uses-grid-container {
  width: 100%;
}

.room-uses-grid {
  display: grid;
  grid-template-columns: repeat(20, 1fr);
  grid-template-rows: repeat(20, 1fr);
  width: 100%;
  height: 100%;
}

.room-uses-title {
  grid-column: 1/21;
  grid-row: 1/6;
  font-size: 5vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: underline;
  font-family: "kanit", sans-serif;
}

.room-uses-data-container1 {
  grid-row: 5/12;
  grid-column: 2/10;
  display: flex;
  flex-direction: column;
  font-size: 3vh;
  font-family: "Dongle", sans-serif;

}

.room-uses-data-container2 {
  grid-row: 5/12;
  grid-column: 13/19;
  display: flex;
  flex-direction: column;
  font-size: 3vh;
  font-family: "Dongle", sans-serif;

}

.logo {
  grid-column: 3/18;
  grid-row: 12/21;
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo img {
  width: 90%;
  height: 90%;
}
</style>