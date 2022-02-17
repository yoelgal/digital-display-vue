<template>
<!--  title
list of options
current week
times for remove, fifth form,fourth form in main -->
  <div class="lunch">
    <div class="lunch-overlay1">
      <h1>Lunch Menu 🍽</h1>
    </div>
    <div class="lunch-overlay2"></div>
    <div class="lunch-overlay3"></div>



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
  grid-row: 4/7;
  grid-column: 5/9;
  overflow: hidden;
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
}

.lunch-overlay1{
  box-shadow: 0vh 0vh 0.1vh 0.7vh #51e847,0vh 0vh 0.1vh 1.6vh #038519;
  grid-row: 1/7;
  background: #0a251a;
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
}

.lunch-overlay2{
  background: #0a251a;
  box-shadow: 0vh 0vh 0.1vh 0.7vh #51e847,0vh 0vh 0.1vh 1.6vh #038519;
  grid-row: 1/11;
  grid-column: 5/11;
  position: relative;
  right: 1vw;
  bottom: 1vh;
  border-bottom-right-radius: 5vh;
  border-bottom-left-radius: 5vh;
  z-index: -1;
}

.lunch-overlay3{
  background: #0a251a;
  box-shadow: 0vh 0vh 0.1vh 0.7vh #51e847,0vh 0vh 0.1vh 1.6vh #038519;
  grid-column: 1/11;
  grid-row: 5/11;
  z-index:-2;
  position: relative;
}



.lunch-grid{
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: repeat(10, 1fr);
  height: 100%;
  width: 100%;
}

.overlay1{
  background-color:white;
  border-top-left-radius: 2vh;
  grid-row: 8/11;
  grid-column: 1/11;
}

.overlay3{
  background-color: white;
  grid-row: 7/10;
  grid-column: 9/11;

}

.overlay2{
  background: #2196f3;
  background: linear-gradient(to bottom right, #1384dc, blue);
  background: #2196f3;
  grid-row: 1/11;
  grid-column: 1/11;
  z-index: -1;


}

.overlay4{
  border-radius: 10vh;
  background: #2196f3;
  grid-row: 6/8;
  grid-column: 8/11;
  z-index: 10;

}

.lunch-title {

  grid-row: 2/3;
  grid-column: 2/6;
  font-size: 2vh;

}

.lunch-underline1{
  background-color: red;
  position: absolute;
  width: 20vw;
  height: 1vh;

}







.icons-items {
  display: flex;
  flex-direction: column;

  height: 100%;
  max-width: 100%;



}

.icons-items div {
  height: 20%;
  display: flex;

  margin-top: 1vh;


}

.icons-items h5 {
  display: inline;
}

.lunchData {
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
  margin-top:1.5vh;
}

.lunchData h4 {
  padding-left: 1vw;
  text-align: left;
  font-size: 3vh;
  text-decoration: underline

}

.lunchData h5 {
  padding-top: 1vh;
  text-align: left;
  margin-left: 1vw;
  padding-left: 0.5vw;
  position: relative;
  bottom: 1vh;
  font-size: 3.5vh;
  height: 6vh;

  border-radius: 2vh;
  line-height: 2.4vh;


}

.size-increase {
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
  bottom: 1vh;

}

</style>