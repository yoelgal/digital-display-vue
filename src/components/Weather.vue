<template>
  <div class="weather">
    <div class="weather-overlay1 border-blue">
      <div class="weather-location">Mill Hill Weather
      </div>
      <div class="w-temperature">
        <p><span style="position: relative;top: 1vh">{{ polledData.current.temp }}</span><sup
            class="temp-blue" style='font-size: 2.5vh;position: relative;bottom: 1vh;font-weight: 600'>°C</sup></p>
      </div>
      <div class="feels-like-text">
        <div>Feels Like:</div>
      </div>
      <div class="feels-like-value">{{ polledData.current.feelsLike }}°C</div>
      <div class="w-wind-icon">
        <!--        <img src='../assets/wind1.png'>-->
        <img src='../assets/wind2.png'>
      </div>
      <div class="w-wind-gust">
        <p><span style="font-weight: 600;">{{ polledData.wind.ms }}</span><span> m/s</span></p>
      </div>
      <div class="wind-speed">
        <p><span style="font-weight: 600;">{{ polledData.wind.kmh }}</span><span> Km/Hr</span></p>
      </div>
      <div class="weather-time">
        <p>⏰ Current hour:</p>
        <p style="font-weight: 400">• {{ polledData.hour }}</p>
      </div>

    </div>
    <div class="weather-overlay2 border-blue">
      <div class="sunrise">
        <img src='../assets/iconmonstr-weather-107-240.png'>
        <h4>{{ polledData.sunrise }}</h4>
      </div>
      <div class="sunset">
        <img src='../assets/iconmonstr-weather-109-240.png'>
        <h4>{{ polledData.sunset }}</h4>
      </div>
    </div>
    <div class="weather-overlay3 border-blue">
      <!--      <img src='../assets/wave-haikei.png'>-->
      <div class="w-data1">
        <p>{{ polledData.forecast[0].time }}</p>
        <h1>{{ polledData.forecast[0].temp }}°C</h1>
        <img :src="polledData.forecast[0].icon" class="weather-data-Icon">
        <h5 class="weather-data-desc">{{ polledData.forecast[0].desc }}</h5>

      </div>
      <div class="w-data2">
        <p>{{ polledData.forecast[1].time }}</p>
        <h1>{{ polledData.forecast[1].temp }}°C</h1>
        <img :src="polledData.forecast[1].icon" class="weather-data-Icon">
        <h5 class="weather-data-desc">{{ polledData.forecast[1].desc }}</h5>
      </div>
      <div class="w-data3">
        <p>{{ polledData.forecast[2].time }}</p>
        <h1>{{ polledData.forecast[2].temp }}°C</h1>
        <img :src="polledData.forecast[2].icon" class="weather-data-Icon">
        <h5 class="weather-data-desc">{{ polledData.forecast[2].desc }}</h5>
      </div>
      <div class="w-data4">
        <p>{{ polledData.forecast[3].time }}</p>
        <h1>{{ polledData.forecast[3].temp }}°C</h1>
        <img :src="polledData.forecast[3].icon" class="weather-data-Icon">
        <h5 class="weather-data-desc">{{ polledData.forecast[3].desc }}</h5>
      </div>
      <div class="w-data5">
        <p>{{ polledData.forecast[4].time }}</p>
        <h1>{{ polledData.forecast[4].temp }}°C</h1>
        <img :src="polledData.forecast[4].icon" class="weather-data-Icon">
        <h5 class="weather-data-desc">{{ polledData.forecast[4].desc }}</h5>
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
      tempThresh: 3,
      polling: null,
      polledData: {
        "hour": "12/24",
        "wind": {
          "ms": 9.77,
          "kmh": 35
        },
        "sunrise": "07:01",
        "sunset": "17:27",
        "current": {
          "temp": 12,
          "feelsLike": 12
        },
        "forecast": [
          {
            "time": "15",
            "temp": 11,
            "desc": "light rain",
            "icon": "http://openweathermap.org/img/wn/10d@2x.png"
          },
          {
            "time": "18",
            "temp": 9,
            "desc": "broken clouds",
            "icon": "http://openweathermap.org/img/wn/04n@2x.png"
          },
          {
            "time": "21",
            "temp": 6,
            "desc": "clear sky",
            "icon": "http://openweathermap.org/img/wn/01n@2x.png"
          },
          {
            "time": "00",
            "temp": 5,
            "desc": "clear sky",
            "icon": "http://openweathermap.org/img/wn/01n@2x.png"
          },
          {
            "time": "03",
            "temp": 4,
            "desc": "clear sky",
            "icon": "http://openweathermap.org/img/wn/01n@2x.png"
          },

        ]
      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const weather = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/weather3')).json());
        this.polledData = weather


      }, 60000)
    }, pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/weather3')
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
.temp-blue{
  color: #2196f3
}

.temp-red {
  /*color: #ff7420;*/
}

.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0.2vh 0.2vh 1vh 0.5vh #1d94d9, 0.5vh 0.3vh 1vh 1vh #4c2bed;

}

.border-red{
  box-shadow: 0.2vh 0.2vh 1vh 0.5vh #ff7420, 0.5vh 0.3vh 1vh 1vh #ed2b2b;
}

.weather {
  grid-column: 1/12;
  grid-row: 1/17;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  color: white;
  background: #2a2828;

}

.weather-overlay1 {
  width: 70%;
  height: 30%;
  background: #2a2828;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #f18f3f, 0.5vh 0.3vh 0.1vh 1vh #d71f56;*/


  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  z-index: 1;
  display: grid;
  grid-template-columns: repeat(20, 1fr);
  grid-template-rows: repeat(20, 1fr);
}

.weather-overlay2 {
  width: 11vw;
  background: #2a2828;
  height: 10vh;
  position: relative;
  bottom: 16vh;
  left: 23vw;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  z-index: -1;
  border-bottom-right-radius: 2vh;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(5, 1fr);
}

.sunrise {
  border-top-left-radius: 2vh;
  border-bottom-left-radius: 2vh;
  border-right: none;
  position: relative;
  left: 2vw;
  top: 1.5vh;
  width: 4.5vw;
  height: 8vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;

}

.sunrise img {
  width: 3vw;
  height: 5vh;
  float: left;
}

.sunrise h4 {
  font-weight: 200;
}

.sunset {
  border-left: none;
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  position: relative;
  top: 1.5vh;
  right: -2vw;
  width: 4.5vw;
  height: 8vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.sunset img {
  width: 3vw;
  height: 5vh;

}

.sunset h4 {
  font-weight: 200;
}

.rain-chance {
  width: 8.5vw;
  height: 8vh;
  position: relative;
  right: 7vw;
  top: 1vh;
}

.rain-chance img {
  position: relative;
  top: 1vh;
  float: left;
  width: 5vw;
  height: 5vh;
}

.rain-chance h1 {
  padding-top: 1vh;
  position: relative;
  left: 0.5vw;
  font-weight: 200;
}


.weather-overlay3 {
  width: 100%;
  height: 80%;
  position: relative;
  bottom: 20vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: space-evenly;
  padding-top: 13vh;
  background: #2a2828;
  z-index: -2;
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  border-top-right-radius: 2vh;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/


}

.weather-overlay3 div {
  background-color: #2a2828;
  width: 10vw;
  height: 23vh;
  margin-left: 1vw;
  margin-right: 1vw;
  border-radius: 3vh;
  position: relative;
  bottom: 1vh;

}

.weather-overlay4 {
  background: white;
  width: 100%;
  height: 100%;
}

.weather-overlay3 p {
  text-align: center;
  color: white;
  font-weight: bold;

}

.weather-overlay3 h1 {
  text-align: center;
  color: white;
  margin-top: 1vh;
  border: 0.2vh solid white;
  border-radius: 2vh;

}

.weather-data-Icon {
  width: 5vw;
  height: 8vh;
  margin-top: 1vh;
  border-bottom: 0.1vh solid white;

}

.weather-overlay3 h5 {
  text-align: center;
  color: white;
  padding-top: 0.5vh;
}


.weather-icon {
  grid-row: 2/5;
  grid-column: 2/5;
}

.weather-icon img {
  width: 5vw;
  height: 6vh;
}


.weather-location {
  grid-row: 3/8;
  grid-column: 2/11;
  font-size: 2.2vh;
  /*border: 2px solid red;*/
}

.w-temperature {
  grid-row: 7/16;
  grid-column: 2/6;
  font-size: 8vh;
}

.w-temperature p {
  position: relative;
  bottom: 2vh;
}

.w-degrees {
  grid-row: 9/11;
  grid-column: 6/7;
  position: relative;
  right: 0.7vw;
  bottom: 1vh;

}

.feels-like-text {
  grid-row: 9/14;
  grid-column: 7/9;
  position: relative;
  left: 0.5vw;
  border-bottom: 0.1vh solid white;
  font-size: 1.5vh;
  font-weight: 500;
}

.feels-like-text div {
  position: relative;
  top: 1vh;
  width: 10vw;
  font-size: 1.5vh;
}


.feels-like-value {
  grid-row: 14/19;
  grid-column: 7/9;
  position: relative;
  left: 0.5vw;
  font-size: 2vh;

}


.w-degrees img {
  width: 1.5vw;
  height: 2vh;
}


.w-wind-icon {
  grid-row: 3/11;
  grid-column: 13/16;
  position: relative;
  right: 1vh;
}

.w-wind-icon img {
  width: 3vw;
  height: 5vh;
}

.w-wind-gust {
  grid-column: 16/19;
  border-bottom: 0.1vh solid white;
  position: relative;
  top: 0.5vh;
  bottom: 0.2vh;
  right: 0.5vw;
  grid-row: 3/6;
  font-weight: 100;

}

.w-wind-gust p {
  position: relative;
  bottom: 0.5vh;
  font-weight: 400;
  font-size: 1.4vh;

}

.wind-speed {
  position: relative;
  top: 0.8vh;
  right: 0.7vh;
  grid-row: 6/9;
  grid-column: 16/20;
  font-size: 1.4vh;
}

.weather-time {
  grid-row: 12/21;
  grid-column: 13/20;
  font-weight: 400;
  position: relative;
  right: 0.5vw;
  font-size: 1.6vh;
}

.weather-grid {
  display: grid;
  grid-template-rows: repeat(20, 1fr);
  grid-template-columns: repeat(20, 1fr);
  height: 100%;
  width: 100%;
}

.temp {
  grid-row: 1/9;
  grid-column: 1/11;
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
  height: 100%;
  width: 100%;
}

.weather-date {
  border: 2px solid blue;
  grid-row: 1/3;
  grid-column: 1/11;
  text-align: center;
  font-size: 3vh;
}

.weather-desc {
  border: 2px solid blue;
  grid-row: 3/6;
  grid-column: 1/11;
}

.temperature {
  border: 2px solid blue;
  grid-row: 6/11;
  grid-column: 1/11;
}


.restOfDay {
  border: 2px solid red;
  grid-column: 1/21;
  grid-row: 9/14;
}

.location {
  border: 2px solid red;
  grid-row: 14/17;
  grid-column: 1/21;
  text-align: center;
  font-size: 6vh;
}

.Mainicon {
  border: 2px solid red;
  grid-row: 1/9;
  grid-column: 11/21;
}


.weather-wave {
  grid-row: 10/21;
  grid-column: 1/21;
}

.weather-wave img {
  height: 100%;
  width: 100%;
}


</style>