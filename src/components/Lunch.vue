<template>
  <div class="lunch">
    <div id='title' class="lunch-title"><h1>LUNCH</h1></div>
    <div class="icons-items">
      <div class='soup'>
        <img src="../assets/cooking-pot.png" width=40 height=50 alt="">
        <div id='lunchData'>
          <h4>Soup Of The Day:</h4>
          <h5 id='size-increase'>{{ polledData.soup }}</h5>
        </div>
      </div>
      <div class='lunch-underline'></div>
      <div class='main'>
        <img src="../assets/hamburger.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Main Meal:</h4>
          <h5 id='size-increase'>{{ polledData.main }}</h5>
        </div>
      </div>
      <div class='lunch-underline'></div>
      <div class='vegetarian'>
        <img src="../assets/fish-simple.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Vegetarian:</h4>
          <h5 id='size-increase'>{{ polledData.veg }}</h5>
        </div>
      </div>

      <div class='lunch-underline'></div>
      <div class='lighter'>
        <img src="../assets/fork-knife.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Lighter Option:</h4>
          <h5 id='size-increase'>{{ polledData.light }}</h5>
        </div>
      </div>
      <div class='lunch-underline'></div>
      <div class='dessert'>
        <img src="../assets/cookie.png" width="40" height="50" alt="">
        <div id='lunchData'>
          <h4>Dessert:</h4>
          <h5 id='size-increase'>{{ polledData.dessert }}</h5>
        </div>
      </div>


    </div>
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
  grid-row: 3/10;
  grid-column: 7/9;
  display: flex;
  flex-direction: column;

}


.lunch-underline {
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

#size-increase {
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