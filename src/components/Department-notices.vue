<template>
  <div class='department-notices'>
    <div class="department-overlay1">
      <h2>💻 Department Notices</h2>
    </div>
    <div class="department-overlay2">
      <ul>
        <li>There are Currently no Computer Science Department Notices. Come back Later!</li>
      </ul>

    </div>
    <div class="department-overlay3">
      <ul>
        <li>There are Currently no Computer Science Department Notices. Come back Later!</li>
      </ul>
      <div class="department-ellipse2"></div>
    </div>
    <div class="department-overlay4">
      <div class="department-name">
        <h2>Computer Science</h2>
      </div>

      <ul>
        <li>There are Currently no Computer Science Department Notices. Come back Later!</li>
      </ul>
      <div class="department-ellipse1"></div>
    </div>


<!--    <div id='title' class='period-title'>-->
<!--      Period:-->
<!--    </div>-->
<!--    <div class='period-number' :class="polledData.period.length>1?'smaller':'regular'">-->
<!--      {{ polledData.period }}-->
<!--    </div>-->
<!--    <div class='period-length'>{{ polledData.range }}</div>-->
  </div>

</template>

<script>
import dayjs from 'dayjs'

export default {
  name: "Period",
  data() {
    return {
      polling: null,
      polledData: {period: 'Period', range: 'loading...'}
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(() => {
        const now = new dayjs().format('HHmm')
        const day = new dayjs().day()
        this.polledData = this.findPeriod(now, day)
      }, 60000)
    },
    findPeriod(time, day) {
      if (day === 5 || day === 6) {
        return {period: 'N/a', range: 'Weekend'}
      } else if (time >= "0900" && time < "0940") {
        return {period: '1', range: '09:00 - 09:40'}
      } else if (time >= "0940" && time < "1020") {
        return {period: '2', range: '09:40 - 10:20'}
      } else if (time >= "1020" && time < "1050") {
        return {period: 'Break', range: '10:20 - 10:50'}
      } else if (time >= "1050" && time < "1130") {
        return {period: '3', range: '10:50 - 11:30'}
      } else if (time >= "1130" && time < "1210") {
        return {period: '4', range: '11:30 - 12:10'}
      } else if (time >= "1210" && time < "1250") {
        return {period: '5', range: '12:10 - 12:50'}
      } else if (time >= "1250" && time < "1340") {
        return {period: 'Lunch', range: '12:50 - 13:40'}
      } else if (time >= "1340" && time < "1420") {
        return {period: '6', range: '13:40 - 14:20'}
      } else if (time >= "1420" && time < "1500") {
        return {period: '7', range: '14:20 - 15:00'}
      } else if (time >= "1500" && time < "1505") {
        return {period: 'Gap', range: '15:00 - 15:05'}
      } else if (time >= "1505" && time < "1545") {
        return {period: '8', range: '15:05 - 15:45'}
      } else if (time >= "1545" && time < "1550") {
        return {period: 'Gap', range: '15:45 - 15:50'}
      } else if (time >= "1550" && time < "1630") {
        return {period: '9', range: '15:50 - 16:30'}
      } else {
        return {period: 'N/a', range: '16:30 - 09:00'}
      }
    }
  },
  mounted() {
    const now = new dayjs().format('HHmm')
    const day = new dayjs().day()
    this.polledData = this.findPeriod(now, day)
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
.department-notices {
  grid-column: 5/8;
  grid-row: 7/10;
  width: 100%;
  height: 100%;
  display:grid;
  grid-template-rows:repeat(20, 1fr);
  grid-template-columns:repeat(20, 1fr);
  overflow: hidden;

}

.department-notices li{
  color: black;
  font-weight: 600;
  font-size: 1.5vh;
  padding-top: 1vh;
  padding-left: 0.2vw;

}

.department-overlay2 li {
  max-width:15vw;
  position: relative;
  left: 1.2vw;
}

.department-overlay3 li {
  position: relative;
  left: 20.5vw;
  max-width:6vw;

}

.department-overlay4 li {
  position: relative;
  left: 18.5vw;
  height: 10vh;
  max-width: 7vw;
  bottom: 4vh;

}

.department-overlay1{
  grid-row: 14/21;
  grid-column: 1/9;
  position: relative;
  right: 1vw;
  background: linear-gradient( to bottom right, rgba(237, 252, 7), rgba(255, 107, 17));
  z-index:1;
  border-top-right-radius: 2vh;
  border-top-left-radius: 2vh;
  box-shadow: 0vh 0vh 0.1vh 0.5vh #fff;

}

.department-overlay1 h2{
  position: relative;
  padding-top: 0.2vh;
  left: 1.3vw;
  font-size: 2.7vh;
}



.department-overlay2{
  grid-row: 5/21;
  grid-column: 1/11;
  border-top-right-radius: 2vh;
  background: linear-gradient(to bottom right, #b37fe8, #d86ce5);
  box-shadow: 0vh 0vh 0.1vh 0.5vh #fff;
}

.department-ellipse1{
  width: 5vw;
  position: relative;
  right: 3vw;
  bottom: 13vh;
  height: 7vh;
  border-radius: 50%;
  background: linear-gradient( to bottom right, rgba(237, 252, 7), rgba(255, 107, 17));

}


.department-ellipse2{
  width: 5vw;
  height: 8vh;
  border-radius: 50%;
  background: linear-gradient( to bottom right, rgba(237, 252, 7), rgba(255, 107, 17));
  position: relative;
  left: 24vw;
  top: 6vh;


}



.department-overlay3{
  grid-row: 1/21;
  grid-column: 5/21;
  background: linear-gradient(to bottom right, #bb8fe8, #d86ce5);
  box-shadow: 0vh 0vh 0.1vh 0.5vh #fafafa;
  border-top-right-radius: 2vh;
  z-index: -1;


}
.department-overlay4{
  grid-row: 1/19;
  position: relative;
  left: 0.2vw;
  border-radius: 2vh;
  grid-column: 1/16;
  z-index:-1;
  background: linear-gradient(to bottom right, #c78cea, #d86ce5);
  box-shadow: 0vh 0vh 0.1vh 0.5vh #fff;
  overflow: hidden;


}

.department-name{
  color: black;
  position: relative;
  left: 3vw;
  max-width:15vw;
}


.department-name h2{
  font-weight: bolder;
  padding-left: 0.5vw;
  font-size: 2.5vh;



}








.period-title {
  font-size: 3.5vh;
  text-align: center;
  text-decoration: underline;
  font-family: "Kanit", sans-serif;
}

.period-number {
  text-align: center;
  position: relative;


}

.regular {
  font-size: 7vh;
}

.smaller {
  font-size: 5vh;
}

.period-length {

  position:relative ;
  top: 2vh;
  font-size: 2vh;
  opacity: 0.7;
  text-align: center;
}

</style>