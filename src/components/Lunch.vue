<template>
<!--
list of options
current week
times for remove, fifth form,fourth form in main -->
  <div class="lunch">

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
  background-color: red;
}






</style>