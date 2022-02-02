<template>
  <div class="room-uses">
    <div class='room-uses-grid-container'>
      <div class='room-uses-grid'>
        <div class='room-uses-title'>Room Uses</div>
        <div class='room-uses-data-container'>
          <table style='position: relative;left: 0.2vw;'>
            <tr>
              <th>IT 1</th>
              <th>IT 2</th>
              <th>IT 3</th>
              <th style='border-right: none;'>IT 4</th>
            </tr>
            <tr>
              <td>10C</td>
              <td>9A</td>
              <td>12A</td>
              <td>13B</td>
            </tr>
          </table>
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
          <img src="../assets/mookle420.png" width="2" height="5" alt="">
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

.room-uses-data-container {
  padding-top: 0.5vh;
  grid-row: 5/12;
  grid-column: 2/19;
  display: flex;
  text-align: center;
  flex-direction: row;
  font-size: 5.2vh;
  font-family: "Dongle", sans-serif;
}

.room-uses-data-container th {
  border-bottom: 0.3vh dashed white;
  border-radius: 2vh;
}

.room-uses-data-container th,
td {
  border-right: 0.3vh dashed white;
  border-top-right-radius: 2vh;
}

.room1,
.room2,
.room3,
.room4 {
  width: 50%;
  height: 100%;
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