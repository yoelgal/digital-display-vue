<template>
  <div class="date-time">
    <div class="date-time-grid">
      <div class='date-time-line1-container'>
        <div class='date-time-line1'></div>
      </div>
      <div class="time">
        <p>{{ hours.local }}:{{ mins }}:{{ secs }}</p>
      </div>
      <dad-joke></dad-joke>
      <div class="date">
        <h1>{{ day }}</h1>
        <br/>
        <h1>{{ date }}</h1>
        <br/>
        <h1>{{ month }}</h1>
      </div>
      <div class="international-times">
        <div>
          <div style="font-size: 3vh; text-align: center;text-decoration: underline;">NYC</div>
          <div>{{ hours.NYC }}:{{ mins }}</div>
        </div>
        <div>
          <div style="font-size: 3vh;text-align: center;text-decoration: underline;">SYD</div>
          <div>{{ hours.SYD }}:{{ mins }}</div>
        </div>
        <div>
          <div style="font-size: 3vh;text-align: center;text-decoration: underline;">TKY</div>
          <div>{{ hours.TKY }}:{{ mins }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import dadJoke from "@/components/Dad-joke";

export default {
  name: "Date-time",
  components: {
    dadJoke
  },
  data() {
    return {
      days: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
      months: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
      polling: null,
      hours: {
        local: "00",
        NYC: "-5",
        SYD: "+11",
        TKY: "+9",
      },
      mins: "00",
      secs: "00",
      day: "day...",
      date: "number...",
      month: "month..."

    }
  },
  methods:
      {
        pollData() {
          this.polling = setInterval(() => {
            const date = new Date()
            //hours
            this.hours.local = date.getHours().toString().padStart(2, '0')
            // this.hours.NYC = this.convertTZ(date, "EST").getHours().toString().padStart(2, '0')
            // this.hours.SYD = this.convertTZ(date, "AEST").getHours().toString().padStart(2, '0')

            this.mins = date.getMinutes().toString().padStart(2, '0')
            this.secs = date.getSeconds().toString().padStart(2, '0')

            this.day = this.days[date.getDay()]
            this.date = date.getDate()
            this.month = this.months[date.getMonth()]
          }, 1000)
        }
        ,
        convertTZ(date, tzString) {
          return new Date((typeof date === "string" ? new Date(date) : date).toLocaleString("en-US", {timeZone: tzString}));
        }
      }
  ,
  beforeDestroy() {
    clearInterval(this.polling)
  }
  ,
  created() {
    this.pollData()
  }
}
</script>

<style scoped>
.date-time {
  grid-column: 9/12;
  grid-row: 4/10;
}

.date-time-grid {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(15, 1fr);
}

.time {
  grid-row: 1/4;
  grid-column: 1/13;
  display: flex;
  justify-content: center;
  align-items: center;
}

.time p {
  margin-top: 4vh;
  font-size: 18vh;
  border-radius: 2vh;
  padding: 1vh;

  font-family: "Dongle", sans-serif;
}


.date {
  grid-column: 1/7;
  grid-row: 8/16;
  text-align: center;
  font-size: 2.3vh;
  font-family: "kanit", sans-serif;
}

.international-times {
  grid-column: 7/13;
  grid-row: 8/16;
  display: flex;
  flex-direction: column;
  font-family: "Dongle", sans-serif;
}

.international-times > div {
  text-align: center;
  height: 33.3%;
  justify-content: space-around;
  align-items: center;
  display: block;
  padding-bottom: 0vh;
  font-size: 6vh;
}

.date-time-line1-container {
  grid-row: 7/8;
  grid-column: 1/13;
  display: flex;
  justify-content: center;
  align-items: center;
}

.date-time-line1 {
  width: 100%;
  height: 0.2vh;

  border-radius: 50%;
  border: 0.4vh solid black;
  background: white;
}

</style>