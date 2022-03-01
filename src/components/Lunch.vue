<template>
<!--
list of options
current week
times for remove, fifth form,fourth form in main -->
  <div class="Lunch">
    <div class="lunch-bg">
      <div class="lunch-overlay1 border-blue">
        <div>Lunch Menu 🍽</div>
      </div>
      <div class="lunch-box">
        <div class="lunch-item">
          <p>Soup Of The Day <span style="font-size: 2vh">🥣</span></p>
          <div>Carrot & Coriander</div>
        </div>
<!--Only use first description for main meal.-->
        <div  class="lunch-item">
          <p>Main Meal<span style="font-size: 2vh"> 🍔</span></p>
          <div>Thai Green Marinated Chicken Breast</div>
        </div>
        <div class="lunch-item">
          <p>Vegetarian<span style="font-size: 2vh"> 🐠</span></p>
          <div>Thai Red Veg Curry</div>
        </div>
        <div class="lunch-item">
          <p>Lighter Option <span style="font-size: 2vh">🥚</span></p>
          <div>Welsh Rarebit Toasts Topped with Chilli Jam & Crispy Onions</div>
        </div>
        <div  class="lunch-item">
          <p>Dessert<span style="font-size: 2vh">🍪</span></p>
          <div>Jam & Coconut Sponge</div>
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
.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0 0 0.1vh 0.7vh #1d94d9, 0 0 0.1vh 1.4vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}


.Lunch {
  grid-row: 10/31;
  grid-column: 24/31;
  overflow: hidden;
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
  color: white;

}
.lunch-bg{
  background: #2a2828;
  grid-row: 1/11;
  grid-column: 1/11;
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
}

.lunch-overlay1{
  grid-row: 1/3;
  grid-column: 2/10;
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius:2vh ;
}

.lunch-overlay1 div {
  font-size: 4.5vh;
  color: white;
  text-align: center;
  font-weight: 500;
}


.lunch-box{
  grid-row: 4/12;
  grid-column: 1/11;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: left;
  justify-content: space-around;
  box-shadow: 0 0 0.1vh 0.7vh #1d94d9, 0 0 0.1vh 1.4vh #4c2bed;
  border-top-right-radius: 6vh;
  border-top-left-radius: 6vh;
}

.lunch-item{
  padding-left: 1vw;
}

.lunch-item p{
  font-weight: 300;
  font-size: 1.3vh;
}

.lunch-item div{
  position: relative;
  font-size: 1.6vh;
  font-weight: 600;





}












</style>