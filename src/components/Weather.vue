<template>
  <div class="weather">
    <div class="sunriseTime">Sunrise: {{ polledData.sunrise }}</div>
    <div class="sunsetTime">Sunset: {{ polledData.sunset}}</div>

    <div class="weather__time" >
      <div class="day__display">{{polledData.forecast[0].time}}</div>
      <img :src="polledData.forecast[0].icon" class="weatherIcon">
      <div class="temp">{{ polledData.forecast[0].temp }}°C</div>
      <div class="weatherDesc">{{ polledData.forecast[0].desc }}</div>
    </div>
    <div class="weather__time" >
      <div class="day__display">{{polledData.forecast[1].time}}</div>
      <img :src="polledData.forecast[1].icon" class="weatherIcon">
      <div class="temp">{{ polledData.forecast[1].temp }}°C</div>
      <div class="weatherDesc">{{ polledData.forecast[2].desc }}</div>
    </div>
    <div class="weather__time" >
      <div class="day__display">{{polledData.forecast[2].time}}</div>
      <img :src="polledData.forecast[2].icon" class="weatherIcon">
      <div class="temp">{{ polledData.forecast[2].temp }}°C</div>
      <div class="weatherDesc">{{ polledData.forecast[2].desc }}</div>
    </div>
    <div class="weather__time" >
      <div class="day__display">{{polledData.forecast[3].time}}</div>
      <img :src="polledData.forecast[3].icon" class="weatherIcon" >
      <div class="temp">{{ polledData.forecast[3].temp }}°C</div>
      <div class="weatherDesc">{{ polledData.forecast[3].desc }}</div>
    </div>
    <div class="weather__time" >
      <div class="day__display">{{polledData.forecast[4].time}}</div>
      <img :src="polledData.forecast[4].icon" class="weatherIcon">
      <div class="temp">{{ polledData.forecast[4].temp }}°C</div>
      <div class="weatherDesc">{{ polledData.forecast[4].desc }}</div>
    </div>

    <ph-sun-horizon :size="32" color="#f88030" weight="bold" />
    <div class="sunriseTime">Sunrise: {{ polledData.sunrise }}</div>
    <div class="sunsetTime">Sunset: {{ polledData.sunset}}</div>


  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Weather",
  data() {
    return {
      polling: null,
      polledData: {
        "sunrise": "2022-01-28T07:45:44.000Z",
        "sunset": "2022-01-28T16:41:44.000Z",
        "dayLengthMins": 536,
        "forecast": [
          {
            "time": "Now",
            "temp": 8,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "00",
            "temp": 8,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "03",
            "temp": 8,
            "desc": "broken clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "06",
            "temp": 9,
            "desc": "broken clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "09",
            "temp": 10,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04d"
          },
          {
            "time": "12",
            "temp": 11,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04d"
          },
          {
            "time": "15",
            "temp": 12,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04d"
          },
          {
            "time": "18",
            "temp": 8,
            "desc": "broken clouds",
            "conditions": "Clouds",
            "icon": "04n"
          }
        ]
      },
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const weather = (await (await fetch('http://localhost:3000/weather')).json());
        this.polledData = weather
        const date = new Date()
        this.polledDate = date
      }, 300000)
    }, pullData() {
      axios
          .get('http://localhost:3000/weather')
          .then(response => (this.polledData = response.data))
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
.weather {
  grid-column: 1/5;
  grid-row: 2/6;
  display: flex;
  flex-direction: column;
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(5, 1fr);
  height: 100%;
  column-gap: 0.1vw;
  font-family: 'Poppins', sans-serif;
  /*background-color: #42b983;*/
}


.weather__time {
  position: relative;
  justify-content: space-around;
  text-align: center;
  margin-top: 2vh;
  grid-row-start: 1;
  grid-row-end: 5;
  padding-left: 0.5vw;
  padding-right: 0.5vw;
}

.day__display {
  font-size: 2vw;
}

.temp {
  font-size: 3vh;
  text-align: center;
  margin-bottom: 1vh;
}



.weatherDesc {
  font-size: 2vh;
  margin-bottom: 1vh;
  max-width: 6.5vw;
  align-content: center;
}

.weatherIcon {
  font-size: 4vh;
  margin-top: 1vh;
}

.sunrise-sunset {
  grid-row: 1/8;
  display: grid;
  grid-template-columns: auto auto;
  gap: 3rem;
}

.sunriseTime {
  font-size: 3vh;
  text-align: left;
  padding-bottom: 3vh;
  padding-left: 2vw;
  grid-column-start: 1;
  grid-column-end: 3;
  grid-row-start: 5;
}
.sunsetTime {
  font-size: 3vh;
  text-align: right;
  padding-bottom: 3vh;
  padding-right: 2vw;
  grid-column-start: 4;
  grid-column-end: 6;
  grid-row-start: 5;
}







.weather-main-grid {
  display: grid;
  grid-template-rows: repeat(15, 1fr);
  grid-template-columns: repeat(15, 1fr);
  height: 100%;
}

.weather-title {
  grid-column: 1/12;
  grid-row: 1/6;

  text-align: left;
  padding-top: 1vh;
  margin-left: 0.3vw;
  font-family: "Kanit", sans-serif;
  text-decoration: underline;
}

.weather-title h2 {
  margin-left: 2vw;
  margin-top: 2vh;
  font-size: 4vh;
}

.weather-other {
  grid-column: 11/15;
  grid-row: 2/5;
  display: flex;
  flex-direction: row;
  border-radius: 3vh;
  width: 15vw;
}

.current-temp {
  width: 80%;
  margin-bottom: 2vh;
  margin-left: 2vw;
  position: relative;
  bottom: 2vh;
}

.current-temp p {
  font-size: 1.5vh;
  padding-left: 0.5vw;
  font-family: "Kanit", sans-serif;
  text-decoration: underline;
}

.current-temp h1 {
  width: 5vw;
  margin-left: 0vw;
  font-size: 6vh;

  border-radius: 50%;
  border: 0.2vh solid black;
  background: #e9ebeb;
  color: #111010;
  padding-left: 1vw;
}

.rain-chance-img {
  width: 2vw;
  height: 4vh;

  position: relative;
  left: 5vw;
  bottom: 5vh;
}

.rain-chance {
  font-family: "Dongle", sans-serif;
  font-size: 4vh;
  position: relative;
  left: 7vw;
  bottom: 10vh;
  color: black;
}

.weather-date-time-container {
  padding-left: 1vw;
  opacity: 0.7;
  grid-row: 3/5;
  grid-column: 1/11;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  font-family: "Saira Condensed", sans-serif;
}

.w-date-time {
  font-size: 2.5vh;
  padding-right: 1.5vw;
}

.weather-grid img {
  margin-bottom: 2vh;
  width: 3vw;
  height: 5vh;
}

.weather-grid {
  grid-column: 1/16;
  grid-row: 6/15;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.weather-grid > div {
  position: relative;
  bottom: 1vh;
  height: 100%;
  width: 15%;
  border-radius: 5vh;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  box-shadow: inset 0.3vh 0.3vh 0.5vh #161414, inset -0.2vh -0.2vh 0.1vh #5a5252;
}

.weather-grid h3 {
  font-family: "Dongle", sans-serif;
  font-size: 2vh;
}

.weather-grid h4 {
  font-size: 3vh;
  font-family: "Dongle", sans-serif;
}

.weather-grid h5 {
  margin-top: 0vh;
  font-family: "Dongle", sans-serif;
  font-size: 2vh;
}

.weather-underline-container {
  grid-column: 1/16;
  grid-row: 15/16;
  margin-bottom: 1vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.weather-underline {
  height: 0.3vh;
  background: rgb(10, 10, 10);
  box-shadow: 0.1vh 0vh 0.5vh #e5edee, -0.1vh 0vh 0.5vh #cacfcf;
  border-radius: 2vh;
  width: 30vw;
  border-radius: 50%;
  border: 0.4vh solid black;
  background: white;
}

.sunrise-sunset-container {
  display: flex;
  flex-direction: row;
  font-size: 2vh;
  justify-content: space-around;
  border: 2px solid red;
}

.sunrise-sunset-container img {
  width: 3vw;
  height: 5vh;
}

.sunrise-container {
  display: flex;
  flex-direction: row;
}

.day-length-countdown {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 0.8vw 0 0.8vw;
}
.sunset-container {
  display: flex;
  flex-direction: row;
}

</style>