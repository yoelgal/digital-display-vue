<template>
  <div class='period-count'>
    <div id='title' class='period-title'>
      Period:
    </div>
    <div class='period-number' :class="polledData.period.length>1?'smaller':'regular'">
      {{ polledData.period }}
    </div>
    <div class='period-length'>{{ polledData.range }}</div>
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
.period-count {
  grid-column: 8/9;
  grid-row: 1/3;
  display: flex;
  flex-direction: column;
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
  top:2vh;
}

.regular {
  font-size: 7vh;
}

.smaller {
  font-size: 5vh;
}

.period-length {

  position:relative ;
  top: 5vh;
  font-size: 2vh;
  opacity: 0.7;
  text-align: center;
}

</style>