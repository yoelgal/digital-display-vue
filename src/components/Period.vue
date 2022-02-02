<template>
  <div class='period-count'>
    <div id='title' class='period-title'>
      Period:
    </div>
    <div class='period-number' :class="polledData.period.length>1?'smaller':'regular'">
      {{polledData.period}}
    </div>
    <div class='period-length'>{{ polledData.lower }} - {{ polledData.upper }}</div>
  </div>
</template>

<script>
import dayjs from 'dayjs'

export default {
  name: "Period",
  data() {
    return {
      polling: null,
      polledData: {period: 'Period', lower: '00:00', upper: '00:00'}
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(() => {
        const now = new dayjs().format('HHmm')
        this.polledData = this.findPeriod(now)
      }, 60000)
    },
    findPeriod(time) {
      if (time >= "0900" && time < "0940") {
        return {period: '1', lower: '09:00', upper: '09:40'}
      } else if (time >= "0940" && time < "1020") {
        return {period: '2', lower: '09:40', upper: '10:20'}
      } else if (time >= "1020" && time < "1050") {
        return {period: 'Break', lower: '10:20', upper: '10:50'}
      } else if (time >= "1050" && time < "1130") {
        return {period: '3', lower: '10:50', upper: '11:30'}
      } else if (time >= "1130" && time < "1210") {
        return {period: '4', lower: '11:30', upper: '12:10'}
      } else if (time >= "1210" && time < "1250") {
        return {period: '5', lower: '12:10', upper: '12:50'}
      } else if (time >= "1250" && time < "1340") {
        return {period: 'Lunch', lower: '12:50', upper: '13:40'}
      } else if (time >= "1340" && time < "1420") {
        return {period: '6', lower: '13:40', upper: '14:20'}
      } else if (time >= "1420" && time < "1500") {
        return {period: '7', lower: '14:20', upper: '15:00'}
      } else if (time >= "1500" && time < "1505") {
        return {period: 'Gap', lower: '15:00', upper: '15:05'}
      } else if (time >= "1505" && time < "1545") {
        return {period: '8', lower: '15:05', upper: '15:45'}
      } else if (time >= "1545" && time < "1550") {
        return {period: 'Gap', lower: '15:45', upper: '15:50'}
      } else if (time >= "1550" && time < "1630") {
        return {period: '9', lower: '15:50', upper: '16:30'}
      } else {
        return {period: 'N/a', lower: '16:30', upper: '09:00'}
      }
    }
  },
  mounted() {
    const now = new dayjs().format('HHmm')
    this.polledData = this.findPeriod(now)
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
}

.regular {
  font-size: 7vh;
}

.smaller {
  font-size: 5vh;
}

.period-length {
  margin-top: 1vh;
  font-size: 2vh;
  opacity: 0.7;
  text-align: center;
}

</style>