<template>
<!--
list of options
current week
times for remove, fifth form,fourth form in main -->
  <div class="Lunch">
    <div class="lunch-bg">
<!--      <div class="lunch-box1 ">-->
<!--        <div class="lunch-item">-->
<!--          <p>Soup Of The Day <span style="font-size: 2vh">🥣</span></p>-->
<!--          <div>Tomato & Roasted Garlic</div>-->
<!--        </div>-->
<!--        <div style="margin-top: 3vh"  class="lunch-item">-->
<!--          <p>Main Meal<span style="font-size: 2vh"> 🍔</span></p>-->
<!--          <div>Tomato & Roasted Garlic</div>-->
<!--        </div>-->
<!--      </div>-->


<!--      <div class="lunch-box2 ">-->
<!--        <div class="lunch-item">-->
<!--        <p>Vegetarian<span style="font-size: 2vh"> 🐠</span></p>-->
<!--        <div>Tomato & Roasted Garlic</div>-->
<!--      </div>-->
<!--        <div style="margin-top: 3vh" class="lunch-item">-->
<!--          <p>Lighter Option <span style="font-size: 2vh">🥚</span></p>-->
<!--          <div>Tomato & Roasted Garlic</div>-->
<!--        </div>-->
<!--      </div>-->

<!--      <div class="soup">-->
<!--        <p>Soup Of The Day <span style="font-size: 2vh">🥣</span></p>-->
<!--        <div>Tomato & Roasted Garlic</div>-->
<!--      </div>-->
    </div>
    <div class="lunch-overlay1 border-blue">
      <div>Lunch Menu 🍽</div>
    </div>
<!--    <div class="lunch-overlay2 border-blue">-->
<!--     -->
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


.lunch-box1{

  grid-row: 3/6;
  position: relative;
  top: 6vh;
  left: 0vw;
  grid-column: 1/6;
  width: 13vw;
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  /*box-shadow: 0 0 0.1vh 0.3vh #1d94d9, 0 0 0.1vh 0.6vh #4c2bed;*/
}

.lunch-box2{
  position: relative;
  top: 6vh;
  left: 3vw;
  grid-row: 3/6;
  height: 18vh;
  grid-column: 6/11;
  border-top-left-radius: 2vh;
  border-bottom-left-radius: 2vh;
  /*box-shadow: 0 0 0.1vh 0.3vh #1d94d9, 0 0 0.1vh 0.6vh #4c2bed;*/
}


.lunch-item{
  position: relative;
  left: 1vw;
  display: flex;
  flex-direction: column;

}
.lunch-item p{
  opacity: 0.5;
  font-weight: 500;
  text-decoration: underline;
}

.lunch-item div{
  position: relative;
  font-size: 1.5vh;
  font-weight: 600;
  max-width: 11vw;



}







.lunch-overlay1{
  grid-row: 1/3;
  grid-column: 2/10;
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius:2vh ;
}

.lunch-overlay1 div {
  font-size: 4vh;
  color: white;
  text-align: center;
  font-weight: 500;
}

.lunch-overlay2{
  grid-row: 6/12;
  grid-column: 1/12;
  border-top-left-radius: 2vh;
  border-top-right-radius:2vh ;
}



</style>