<template>
  <div class="room-uses">
<!--    <div class="room-overlay1">-->
<!--      <h1>🗓 Room Uses</h1>-->
<!--    </div>-->
<!--    <div class="room-overlay2">-->
<!--      <h1>IT 1:-->
<!--      <br>-->
<!--        10C-->
<!--      </h1>-->

<!--    </div>-->
<!--    <div class="room-overlay3">-->
<!--      <h1>IT 1:-->
<!--        <br>-->
<!--        10C-->
<!--      </h1>-->
<!--    </div>-->
<!--    <div class="room-overlay4">-->
<!--      <h1>IT 1:-->
<!--        <br>-->
<!--        10C-->
<!--      </h1>-->
<!--    </div>-->
<!--    <div class="room-overlay5">-->
<!--      <h1>IT 1:-->
<!--        <br>-->
<!--        10C-->
<!--      </h1>-->
<!--    </div>-->
<!--    <div class='room-uses-grid-container'>-->
<!--      <div class='room-uses-grid'>-->
<!--        <div class='room-uses-title'>Room Uses</div>-->
<!--        <div class='room-uses-data-container1'>-->
<!--          <ul style="margin-left: 1vw">-->
<!--            <li>IT 1:</li>-->
<!--            <p style="display:block">Unavailable</p>-->
<!--            <li>IT 2:</li>-->
<!--            <p>Unavailable</p>-->
<!--          </ul>-->
<!--        </div>-->
<!--        <div class='room-uses-data-container2'>-->
<!--          <ul>-->
<!--            <li>IT 3:</li>-->
<!--            <p style="display:block">Unavailable</p>-->
<!--            <li>IT 4:</li>-->
<!--            <p>Unavailable</p>-->
<!--          </ul>-->
<!--        </div>-->
<!--        <div class="room-quote-line">-->
<!--          <hr>-->
<!--        </div>-->
<!--        <div class="daily-quoteXX">-->
<!--          <div class="facts-title-bar">-->
<!--            <ion-icon style="padding-left: 1vw" class="book-icon" name="book"></ion-icon>-->
<!--            <div  class='fact-title'>Daily Quote</div>-->
<!--            <ion-icon style="padding-right: 1vw" class="book-icon" name="book"></ion-icon>-->

<!--          </div>-->
<!--          <div class="daily-fact-container">-->
<!--            <div class="daily-fact" :class="polledData.text.length>100?'smaller': 'regular'">-->
<!--              <p>-->
<!--                {{polledData.text}} - {{polledData.author}}-->
<!--              </p>-->

<!--            </div>-->
<!--          </div>-->
<!--        </div>-->



<!--      </div>-->
<!--    </div>-->

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
        const fact = (await (await fetch('https://mhs-main.herokuapp.com/quotes')).json()).cs;
        this.polledData = fact
      }, 86400000)
    },
    pullData() {
      axios
          .get('https://mhs-main.herokuapp.com/quotes')
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
  position: absolute;
  top: 30vh;
  left: 50vw;
  display:grid;
  grid-template-rows:repeat(20, 1fr);
  grid-template-columns:repeat(20, 1fr);
  background: red;
  z-index: 10;


}

.room-uses > div {

  box-shadow: 0vh 0vh 0.1vh 0.5vh #fff;
}

.room-overlay1{
  grid-row: 1/8;
  grid-column: 13/21;
  border-bottom-left-radius: 2vh;
  background: linear-gradient(to bottom right, #e8e50e, #ee743f);
}
.room-overlay1 h1{
  padding-left: 0.5vw;
  padding-top: 1vh;
}


.room-overlay2{
  grid-row: 10/21;
  grid-column: 1/8;
  border-top-right-radius: 2vh;
  background:linear-gradient(to bottom right, #64e564, #3de00f);
}

.room-overlay2 h1{
  padding-left: 1vw;
  font-size: 5.5vh;
}

.room-overlay3{
  grid-column: 7/15;
  grid-row: 11/21;
  background:linear-gradient(to bottom right, #64e564, #39e10a);
  z-index:-2;
  border-top-right-radius:2vh;
}

.room-overlay3 h1{
  padding-left: 2.5vw;
  font-size: 5.4vh;
}


.room-overlay4{
  grid-column: 1/9;
  grid-row: 1/12;
  background:linear-gradient(to bottom right, #64e564, #92cc56);
  z-index:-1;
  border-bottom-right-radius: 2vh;
  position: relative;
  left: 0.2vw;
}

.room-overlay4 h1{
  padding-left: 1vw;
  font-size: 4.7vh;
}


.room-overlay5{
  grid-row: 1/12;
  grid-column: 8/14;
  background:linear-gradient(to bottom right, #64e564, #9cd263);
  z-index:-3;
}

.room-overlay5 h1{
  padding-left: 1.85vw;
  padding-top: 1vh;
  font-size: 4vh;
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