<template>
  <div class="lunch">
    <div id='title' class="lunch-title"><h1>LUNCH</h1></div>
    <div class="icons-items">
      <div class='soup'>
        <img src="../assets/cooking-pot.png" width=40 height=50 alt="">
        <div id='lunchData'>
          <h4>Soup Of The Day:</h4>
          <h5  id = 'size-increase' >x x x x x x x x x x</h5>
        </div>
      </div>
      <div class='lunch-underline'></div>
      <div class='main'>
        <img src="../assets/hamburger.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Main Meal:</h4>
          <h5 id = 'size-increase'>x x x x x x x x x x</h5>
        </div>
      </div>
      <div class='lunch-underline'></div>
      <div class='vegetarian'>
        <img src="../assets/fish-simple.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Vegetarian:</h4>
          <h5 id = 'size-increase' >x x x x x x x x x x</h5>
        </div>
      </div>

      <div class='lunch-underline'></div>
      <div class='lighter'>
        <img src="../assets/fork-knife.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Lighter Option:</h4>
          <h5  id = 'size-increase' >x x x x x x x x x x</h5>
        </div>
      </div>
      <div class='lunch-underline'></div>
      <div class='dessert'>
        <img src="../assets/cookie.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Dessert:</h4>
          <h5  id = 'size-increase' >x x x x x x x x x x</h5>
        </div>
      </div>



    </div>
  </div>
</template>

<script>
export default {
  name: "Lunch"
}
</script>

<style>
.lunch {
  grid-row: 3/10;
  grid-column: 7/9;
  display: flex;
  flex-direction: column;

}


.lunch-underline{
  width: 90%;
  margin: auto;
  height: 0.2vh;
  margin-top: 2vh;
  margin-bottom: 2vh;
  border: 2px solid black;
  border-radius: 2vh;
}

.lunch-title {
  height: 25%;
  letter-spacing: 0.7vw;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 3vh;
  font-family: "kanit", sans-serif;
  text-decoration: underline;
}

.icons-items {
  display: flex;
  flex-direction: column;
  /* grid-template-columns: repeat(10, 1fr); */
  height: 100%;
  max-width: 100%;

}

.icons-items div {
  height: 20%;
  display: flex;
  flex-direction: row;
}

.icons-items h5 {
  display: inline;
}

#lunchData {
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
  text-align: center;
  font-family: "Dongle", sans-serif;


}



.lunch img {
  width: 3vw;
  height: 5vh;
  padding-left: 0.5vw;
}

#lunchData h4 {
  padding-left: 1vw;
  text-align: left;
  font-size: 3vh;
}
#lunchData h5 {
  text-align: left;
  padding-left: 1vw;
  position: relative;
  bottom: 1vh;
  font-size: 3.5vh;

}

#size-increase{
  font-size: 4vh;
}

.soup {

}

.main {
}

.vegetarian {
}

.lighter {
}

.dessert {

  position: relative;
  bottom: 2vh;

}

</style>