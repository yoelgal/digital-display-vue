<template>
  <div class="weather">
    <div class="weather-grid">
      <div class="weather-grid-container">
        <div class="weather__time">
          <div class="day__display">{{ polledData.forecast[0].time }}</div>
          <img :src="polledData.forecast[0].icon" class="weatherIcon">
          <div class="temp">{{ polledData.forecast[0].temp }}°C</div>
          <div class="weatherDesc">{{ polledData.forecast[0].desc }}</div>
        </div>
        <div class="weather__time">
          <div class="day__display">{{ polledData.forecast[1].time }}</div>
          <img :src="polledData.forecast[1].icon" class="weatherIcon">
          <div class="temp">{{ polledData.forecast[1].temp }}°C</div>
          <div class="weatherDesc">{{ polledData.forecast[2].desc }}</div>
        </div>
        <div class="weather__time">
          <div class="day__display">{{ polledData.forecast[2].time }}</div>
          <img :src="polledData.forecast[2].icon" class="weatherIcon">
          <div class="temp">{{ polledData.forecast[2].temp }}°C</div>
          <div class="weatherDesc">{{ polledData.forecast[2].desc }}</div>
        </div>
        <div class="weather__time">
          <div class="day__display">{{ polledData.forecast[3].time }}</div>
          <img :src="polledData.forecast[3].icon" class="weatherIcon">
          <div class="temp">{{ polledData.forecast[3].temp }}°C</div>
          <div class="weatherDesc">{{ polledData.forecast[3].desc }}</div>
        </div>
        <div class="weather__time">
          <div class="day__display">{{ polledData.forecast[4].time }}</div>
          <img :src="polledData.forecast[4].icon" class="weatherIcon">
          <div class="temp">{{ polledData.forecast[4].temp }}°C</div>
          <div class="weatherDesc">{{ polledData.forecast[4].desc }}</div>
        </div>
      </div>

      <div class="bottom_bar">
        <div class="sunrise">
          <!--        <img src="https://img.icons8.com/ios/50/000000/sunrise--v1.png" class="bottom_icon">-->
                  <img src="../assets/iconmonstr-weather-107-240.png" class="bottom_icon">
          <div class="sun__time">{{ polledData.sunrise }}</div>
        </div>
        <div class="sunset">
          <!--        <img src="https://img.icons8.com/ios/100/000000/sunset--v1.png" class="bottom_icon">-->
                  <img src="../assets/iconmonstr-weather-109-240.png" class="bottom_icon">
          <div class="sun__time">{{ polledData.sunset }}</div>
        </div>
      </div>

    </div>



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
        const weather = (await (await fetch('https://digital-display-express.herokuapp.com/weather')).json());
        this.polledData = weather
      }, 300000)
    }, pullData() {
      axios
          .get('https://digital-display-express.herokuapp.com/weather')
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
  font-family: 'Poppins', sans-serif;

}

.weather-grid {
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
  width: 100%;
  height: 100%;

}

.weather-grid-container {
  grid-column: 1/11;
  grid-row:1/8;
  display: flex;
  justify-content: space-around;
  align-items: center;

}


.weather__time {
  /*display: flex;*/
  flex-direction: column;
  justify-content: space-around;
  text-align: center;
  height: 25vh;

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
  height: 10vh;
}

.sunrise {

  text-align: center;
  grid-column-start: 2;
  /*box-shadow: inset 0.3vh 0.3vh 0.5vh #161414, inset -0.2vh -0.2vh 0.1vh #5a5252;*/
  border-style: solid;
  border-width: 2px;
  border-color: #7f8fa6;
  border-radius: 4.7vh;
  background-color: #273c75;;
  margin-bottom: 3vh;
  padding: 0.5vh 2vh 0.5vh 2vh;



}

.sunset {

  text-align: center;
  grid-column-start: 4;
  /*border-style: inset;*/
  border-style: solid;
  border-color: #7f8fa6;
  border-radius: 4.7vh;
  background-color: #273c75;
  border-width: 2px;

  margin-bottom: 3vh;
  padding: 0.5vh 2vh 0.5vh 2vh;

}

.sun__time {
  font-size: 3vh;
  padding-bottom: 1vh;
  grid-row: 2/2;

}

.bottom_icon {
  margin-top: 0.5vh;
  height: 6vh;
  margin-bottom: 0vh;
  grid-row: 1/2;

}

.bottom_bar {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  grid-row: 8/11;
  grid-column: 1/11;


}


</style>