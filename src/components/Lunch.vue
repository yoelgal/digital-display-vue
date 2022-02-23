<template>
<!--
list of options
current week
times for remove, fifth form,fourth form in main -->
  <div class="lunch">
<!--    <div class="lunch-overlay1">-->
<!--      <h1>Lunch Menu</h1>-->
<!--      <img src=../assets/dish-plate.png>-->
<!--    </div>-->
<!--    <div class="lunch-overlay2">-->
<!--       <div class="lunch-options-container">-->
<!--          <div class="soup">-->
<!--&lt;!&ndash;            <img width="40vw" height="40vh" src='../assets/cooking-pot.png'>&ndash;&gt;-->
<!--            <h1>🥣</h1>-->
<!--            <h4>Soup Of The Day</h4>-->
<!--            <h5>x x x x x x x x x x </h5>-->
<!--          </div>-->
<!--          <div class="main-meal">-->
<!--&lt;!&ndash;            <img width="40vw" height="40vh" src='../assets/hamburger.png'>&ndash;&gt;-->
<!--            <h1>🍔</h1>-->
<!--            <h4>Soup Of The Day</h4>-->
<!--            <h5>x x x x x x x x x x </h5>-->
<!--          </div>-->
<!--          <div class="vegetarian">-->
<!--&lt;!&ndash;            <img width="40vw" height="40vh" src='../assets/fish-simple.png'>&ndash;&gt;-->
<!--            <h1>🐟</h1>-->
<!--            <h4>Soup Of The Day</h4>-->
<!--            <h5>x x x x x x x x x x </h5>-->
<!--          </div>-->
<!--          <div class="lighter">-->
<!--            <h1>🥚</h1>-->
<!--            <h4>Soup Of The Day</h4>-->
<!--            <h5>x x x x x x x x x x </h5>-->
<!--          </div>-->
<!--          <div class="dessert">-->
<!--            <h1>🍪</h1>-->
<!--            <h4>Soup Of The Day</h4>-->
<!--            <h5>x x x x x x x x x x </h5>-->
<!--          </div>-->
<!--       </div>-->
<!--    </div>-->
<!--    <div class="lunch-overlay3"></div>-->



<!--   </div>-->


<!--    <div  class="lunch-title"><h1>LUNCH</h1></div>-->
<!--    <div class="icons-items">-->
<!--      <div class='soup'>-->
<!--        <img src="../assets/cooking-pot.png" width=512 height=512 alt="">-->
<!--        <div class='lunchData'>-->
<!--          <h4>Soup Of The Day:</h4>-->
<!--          <h5 class='size-increase'>{{ polledData.soup }}</h5>-->
<!--        </div>-->
<!--      </div>-->
<!--      <hr>-->

<!--      <div class='main'>-->
<!--        <img src="../assets/hamburger.png" width="512" height="512" alt="">-->
<!--        <div class='lunchData'>-->
<!--          <h4>Main Meal:</h4>-->

<!--          <h5 class='size-increase'>{{ polledData.main }}</h5>-->

<!--        </div>-->
<!--      </div>-->
<!--      <hr>-->
<!--      <div class='vegetarian'>-->
<!--        <img src="../assets/fish-simple.png" width="512" height="512" alt="">-->
<!--        <div class='lunchData'>-->
<!--          <h4>Vegetarian:</h4>-->
<!--          <h5 class='size-increase'>{{ polledData.veg }}</h5>-->
<!--        </div>-->
<!--      </div>-->

<!--      <hr>-->
<!--      <div class='lighter'>-->
<!--        <img src="../assets/fork-knife.png" width="512" height="512" alt="">-->
<!--        <div class='lunchData'>-->
<!--          <h4>Lighter Option:</h4>-->
<!--          <h5 class='size-increase'>{{ polledData.light }}</h5>-->
<!--        </div>-->
<!--      </div>-->
<!--      <hr>-->
<!--      <div class='dessert'>-->
<!--        <img src="../assets/cookie.png" width="512" height="512" alt="">-->
<!--        <div class='lunchData'>-->
<!--          <h4>Dessert:</h4>-->
<!--          <h5 class='size-increase'>{{ polledData.dessert }}</h5>-->
<!--        </div>-->
<!--      </div>-->


<!--    </div>-->
  </div>
</template>

<script>
import axios from "axios";
import dayjs from "dayjs";

export default {
  name: "Lunch",
  data() {
    return {
      polledData: {
        soup: "Loading...",
        main: "Loading...",
        veg: "Loading...",
        light: "Loading...",
        dessert: "Loading..."
      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const day = new dayjs().day()
        const menu = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/lunch-menu')).json());
        this.polledData = {
          soup: menu.lunchMenu.mainLunch[menu.week - 1][day].soup,
          main: menu.lunchMenu.mainLunch[menu.week - 1][day].main,
          veg: menu.lunchMenu.mainLunch[menu.week - 1][day].veg,
          light: menu.lunchMenu.mainLunch[menu.week - 1][day].light,
          dessert: menu.lunchMenu.mainLunch[menu.week - 1][day].dessert
        }
      }, 10000)
    },
    pullData() {
      const day = new dayjs().day()
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/lunch-menu')
          .then(response => (this.polledData = {
            soup: response.data.lunchMenu.mainLunch[response.data.week - 1][day].soup,
            main: response.data.lunchMenu.mainLunch[response.data.week - 1][day].main,
            veg: response.data.lunchMenu.mainLunch[response.data.week - 1][day].veg,
            light: response.data.lunchMenu.mainLunch[response.data.week - 1][day].light,
            dessert: response.data.lunchMenu.mainLunch[response.data.week - 1][day].dessert
          }))
      console.log(day)
    }
  },
  mounted() {
    this.pullData()
  },
  beforeDestroy() {
    clearInterval(this.polling)
  },
  created() {
    this.pollData()
  }

}
</script>

<style>
.lunch {
  grid-row: 9/25;
  grid-column: 12/22;
  overflow: hidden;
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
}

.lunch-overlay1{
  box-shadow:0vh 0vh 0.1vh 0.5vh #bb799a,0vh 0vh 0.1vh 0.7vh #950740,0vh 0vh 0.1vh 1.5vh #c3073f;
  grid-row: 1/7;
  background: #1a1a1d;
  grid-column: 1/6;
  position: relative;
  top: 1vh;
  right: 1vw;
  border-bottom-right-radius: 10vh;
  border-top-right-radius: 10vh;
}

.lunch-overlay1 h1{
  position: relative;
  left: 2vw;
  font-size: 5.5vh;
  color: white;
  font-weight: 400;
}

.lunch-overlay1 img{
  position: relative;
  left: 11.5vw;
  bottom: 8vh;
  width: 3vw;
  height: 6vh;
}

.lunch-overlay2{
  background: #1a1a1d;
  box-shadow:0vh 0vh 0.1vh 0.5vh #bb799a,0vh 0vh 0.1vh 0.7vh #950740,0vh 0vh 0.1vh 1.5vh #c3073f;
  grid-row: 1/11;
  grid-column: 5/11;
  position: relative;
  right: 1vw;
  bottom: 1vh;
  border-bottom-right-radius: 5vh;
  border-bottom-left-radius: 5vh;
  z-index: -1;
}

.lunch-overlay2 h1{
  border: 2px solid white;
  border-radius: 2vh;
  position: relative;
  right: 0.5vw;
  padding-left: 0.6vw;
  width: 3.5vw;
  height: 4.7vh;
}

.lunch-options-container{
  border-radius: 2vh;
  width: 15vw;
  height: 26vh;
  position: relative;
  left: 5vw;
  top: 2vh;
  display: flex;
  flex-direction: column;
}

.lunch-options-container div{
  width: 90%;
  height: 18%;
  margin-top: 0.6vh;
}

.soup{
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(4, 1fr);
  width: 100%;
  height: 100%;
}

.main-meal{
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(4, 1fr);
  width: 100%;
  height: 100%;

}
.vegetarian{
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(4, 1fr);
  width: 100%;
  height: 100%;

}
.lighter{
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(4, 1fr);
  width: 100%;
  height: 100%;

}
.dessert{
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(4, 1fr);
  width: 100%;
  height: 100%;
}



.lunch-options-container h4{
  grid-row: 1/3;
  grid-column: 2/5;
  color: white;
  font-weight: 200;
}
.lunch-options-container h5{
  position: relative;
  bottom: 2vh;
  grid-column: 2/5;
  color: white;
  font-weight: 200;
}


/*.lunch-options-container h4{*/
/*  border: 2px solid gold;*/
/*  color: white;*/
/*  font-weight: 200;*/
/*  grid-row: 1/7;*/
/*}*/

/*.lunch-options-container h5{*/
/*  color: white;*/
/*  font-weight: 200;*/
/*  position: relative;*/
/*  top: 10vh;*/
/*  border: 2px solid white;*/
/*  width: 20vw;*/
/*}*/





</style>