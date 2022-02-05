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
        <div class="room-quote-line">
          <hr>
        </div>
        <div class="daily-quoteXX">
          <div class="facts-title-bar">
            <ion-icon style="padding-left: 1vw" class="book-icon" name="book"></ion-icon>
            <div  class='fact-title'>Daily Quote</div>
            <ion-icon style="padding-right: 1vw" class="book-icon" name="book"></ion-icon>

          </div>
          <div class="daily-fact-container">
            <div class="daily-fact" :class="polledData.text.length>100?'smaller': 'regular'">
              <p>
                {{polledData.text}} - {{polledData.author}}
              </p>

            </div>
          </div>
        </div>



      </div>
    </div>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name1: "Room-uses",
  name: "Facts",
  data() {
    return {
      polling: null,
      polledData: {
        text: 'Loading quote...',
        author: 'Loading author...'
      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const fact = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/quotes')).json()).cs;
        this.polledData = fact
      }, /*86400000*/ 10000)
    },
    pullData() {
      axios
          .get('https://digital-display-express.herokuapp.com/quotes')
          .then(response => (this.polledData = response.data.cs))
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

<style scoped>
.room-uses {
  grid-column: 5/7;
  grid-row: 3/10;
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
  grid-row: 1/4;
  font-size: 5vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: underline;
  font-family: "kanit", sans-serif;

}

.room-uses-data-container1 {
  grid-row: 4/10;
  grid-column: 2/10;
  display: flex;
  flex-direction: column;
  font-size: 3vh;
  font-family: "Dongle", sans-serif;


}

.room-uses-data-container2 {
  grid-row: 4/10;
  grid-column: 13/19;
  display: flex;
  flex-direction: column;
  font-size: 3vh;
  font-family: "Dongle", sans-serif;

}

.room-quote-line{
  grid-row: 10/12;
  grid-column: 1/21;
  padding-top: 3vh;
}

.daily-quoteXX {
  grid-column: 1/21;
  grid-row: 11/21;


}
.facts-title-bar {
  display: flex;
  justify-content: center;
  align-items: center;

}

.fact-title {
  letter-spacing: 1vh;
  font-size: 3vh;
  text-align: center;
  text-decoration: underline;
  font-family: "Kanit", sans-serif;

}

.book-icon {
  padding-top: 1vh;
  height: 5vh;
  width: 3vw;

}

.daily-fact-container {
  width: 100%;
  height: 70%;
  text-align: center;


}

.daily-fact p {
  margin-top: 3vh;
  display: block;
  font-family: "Kanit", sans-serif;
  align-self: center;
  vertical-align: middle;
  padding-top: 2%;
  padding-left: 6%;
  padding-right: 6%;
  justify-content: center;
  /* font-family: "Dongle", sans-serif; */
}

.regular {
  font-size: 2.5vh;
}

.smaller {
  font-size: 2vh;
}

</style>