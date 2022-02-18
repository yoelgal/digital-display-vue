<template>
  <div class="weather">
    <div class="weather-overlay1">
      <div class="weather-location">Mill Hill Weather
      </div>
      <div class="w-temperature">
        <p><span style="position: relative;top: 1vh">12</span><sup style='font-size: 2.5vh;position: relative;bottom: 1vh;color: #ff6c05;font-weight: 600'>°C</sup></p>
      </div>
      <div  class="w-max">️↑ <span style="font-weight: 400"> 15</span></div>
      <div  class="w-min">↓ <span style="font-weight: 400"> 9</span></div>
      <div class="w-wind-icon">
<!--        <img src='../assets/wind1.png'>-->
        <img src='../assets/wind2.png'>
      </div>
      <div class="w-wind-gust">
        <p ><span  style="font-weight: 400;">7.33</span><span> m/s</span></p>
      </div>
      <div class="wind-speed">
        <p><span  style="font-weight: 400;">19</span><span> Km/Hr</span></p>
      </div>
      <div class="weather-time">
        <p>Current hour:</p>
        <p style="font-weight: 400">• 16/24</p>
      </div>

    </div>
    <div class="weather-overlay2">
      <div class="sunrise">
        <img src='../assets/iconmonstr-weather-107-240.png'>
        <h4>7:30</h4>
      </div>
      <div class="sunset">
        <img src='../assets/iconmonstr-weather-109-240.png'>
        <h4>9:30</h4>
      </div>
    </div>
    <div class="weather-overlay3">
<!--      <img src='../assets/wave-haikei.png'>-->
        <div class="w-data1">
          <p>{{ polledData.forecast[1].time }}</p>
          <h1>{{ polledData.forecast[1].temp }}°C</h1>
          <img :src="polledData.forecast[1].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[1].desc }}</h5>

        </div>
        <div class="w-data2">
          <p>{{ polledData.forecast[2].time }}</p>
          <h1>{{ polledData.forecast[2].temp }}°C</h1>
          <img :src="polledData.forecast[2].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[2].desc }}</h5>
        </div>
        <div class="w-data3">
          <p>{{ polledData.forecast[3].time }}</p>
          <h1>{{ polledData.forecast[3].temp }}°C</h1>
          <img :src="polledData.forecast[3].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[3].desc }}</h5>
        </div>
        <div class="w-data4">
          <p>{{ polledData.forecast[4].time }}</p>
          <h1>{{ polledData.forecast[4].temp }}°C</h1>
          <img :src="polledData.forecast[4].icon" class="weather-data-Icon">

          <h5 class="weather-data-desc">{{ polledData.forecast[4].desc }}</h5>
        </div>
        <div class="w-data5">
          <p>{{ polledData.forecast[5].time }}</p>
          <h1>{{ polledData.forecast[5].temp }}°C</h1>
          <img :src="polledData.forecast[5].icon" class="weather-data-Icon">
          <h5 class="weather-data-desc">{{ polledData.forecast[5].desc }}</h5>

        </div>


    </div>

<!--    <div class="weather-grid">-->
<!--      <div class="weather-wave">-->
<!--        <img src="../assets/wave1.png">-->
<!--      </div>-->
<!--      <div class="temp">-->
<!--        <div class="weather-date">SAT FEB 12</div>-->
<!--        <div class="weather-desc"></div>-->
<!--        <div class="temperature"></div>-->
<!--      </div>-->
<!--      <div class="restOfDay"></div>-->
<!--      <div class="location">Mill Hill School</div>-->
<!--      <div class="Mainicon"></div>-->


      <!--        <div class="futureData">-->
      <!--        <div   class="weather__time">-->
      <!--          <div class="day__display">{{ polledData.forecast[1].time }}</div>-->
      <!--          <img :src="polledData.forecast[1].icon" class="weatherIcon">-->
      <!--          <div class="temp">{{ polledData.forecast[1].temp }}°C</div>-->
      <!--          <div class="weatherDesc">{{ polledData.forecast[2].desc }}</div>-->
      <!--        </div>-->
      <!--        <div  class="weather__time">-->
      <!--          <div class="day__display">{{ polledData.forecast[2].time }}</div>-->
      <!--          <img :src="polledData.forecast[2].icon" class="weatherIcon">-->
      <!--          <div class="temp">{{ polledData.forecast[2].temp }}°C</div>-->
      <!--          <div class="weatherDesc">{{ polledData.forecast[2].desc }}</div>-->
      <!--        </div>-->
      <!--        <div class="weather__time">-->
      <!--          <div class="day__display">{{ polledData.forecast[3].time }}</div>-->
      <!--          <img :src="polledData.forecast[3].icon" class="weatherIcon">-->
      <!--          <div class="temp">{{ polledData.forecast[3].temp }}°C</div>-->
      <!--          <div class="weatherDesc">{{ polledData.forecast[3].desc }}</div>-->
      <!--        </div>-->
      <!--        <div class="weather__time">-->
      <!--          <div class="day__display">{{ polledData.forecast[4].time }}</div>-->
      <!--          <img :src="polledData.forecast[4].icon" class="weatherIcon">-->
      <!--          <div class="temp">{{ polledData.forecast[4].temp }}°C</div>-->
      <!--          <div class="weatherDesc">{{ polledData.forecast[4].desc }}</div>-->
      <!--        </div>-->
      <!--        </div>-->

      <!--      <div class="weather-underline">-->
      <!--        <div></div>-->
      <!--      </div>-->
      <!--      <div class="bottom_bar">-->

      <!--        <div class="sunrise">-->
      <!--          &lt;!&ndash;        <img src="https://img.icons8.com/ios/50/000000/sunrise&#45;&#45;v1.png" class="bottom_icon">&ndash;&gt;-->
      <!--                  <img src="../assets/iconmonstr-weather-107-240.png" class="bottom_icon">-->
      <!--          <div class="sun__time">{{ polledData.sunrise }}</div>-->
      <!--        </div>-->
      <!--        <div class="sunset">-->
      <!--          &lt;!&ndash;        <img src="https://img.icons8.com/ios/100/000000/sunset&#45;&#45;v1.png" class="bottom_icon">&ndash;&gt;-->
      <!--                  <img src="../assets/iconmonstr-weather-109-240.png" class="bottom_icon">-->
      <!--          <div class="sun__time">{{ polledData.sunset }}</div>-->
      <!--        </div>-->
      <!--      </div>-->

<!--    </div>-->



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
        "sunrise": "null",
        "sunset": "null",
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
            "time": "00:00",
            "temp": 8,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "03:00",
            "temp": 8,
            "desc": "broken clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "06:00",
            "temp": 9,
            "desc": "broken clouds",
            "conditions": "Clouds",
            "icon": "04n"
          },
          {
            "time": "09:00",
            "temp": 10,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04d"
          },
          {
            "time": "12:00",
            "temp": 11,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04d"
          },
          {
            "time": "15:00",
            "temp": 12,
            "desc": "overcast clouds",
            "conditions": "Clouds",
            "icon": "04d"
          },
          {
            "time": "18:00",
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
        const weather = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/weather')).json());
        this.polledData = weather
      }, 300000)
    }, pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/weather')
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
  grid-column: 1/5 ;
  grid-row: 1/6;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  color: white;
  background: #2a2828;

}

.weather-overlay1{
  width: 70%;
  height: 30%;
  background: #2a2828;
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #f18f3f, 0.5vh 0.3vh 0.1vh 1vh #d71f56;
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  z-index: 1;
  display: grid;
  grid-template-columns: repeat(20, 1fr);
  grid-template-rows: repeat(20, 1fr);
}

.weather-overlay2{
  width: 11vw;
  background: #2a2828;
  height: 10vh;
  position: relative;
  bottom: 16vh;
  left: 23vw;
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #f18f3f, 0.5vh 0.3vh 0.1vh 1vh #d71f56;
  z-index:-1;
  border-bottom-right-radius: 2vh;
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(5, 1fr);
}

.sunrise{
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

.sunrise img{
  width: 3vw;
  height: 5vh;
  float: left;
}
.sunrise h4{
  font-weight: 200;
}

.sunset{
  border-left: none;
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  position: relative;
  top: 1.5vh;
  right: -2vw;
  width:4.5vw ;
  height: 8vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.sunset img{
  width: 3vw;
  height: 5vh;

}

.sunset h4{
  font-weight: 200;
}

.rain-chance{
  width: 8.5vw;
  height: 8vh;
  position: relative;
  right: 7vw;
  top: 1vh;
}

.rain-chance img{
  position: relative;
  top: 1vh;
  float: left;
  width: 5vw;
  height: 5vh;
}

.rain-chance h1{
  padding-top: 1vh;
  position: relative;
  left: 0.5vw;
  font-weight: 200;
}


.weather-overlay3{
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
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #f18f3f, 0.5vh 0.3vh 0.1vh 1vh #d71f56;



}

.weather-overlay3 div {
  background-color: #2a2828;
  width: 10vw;
  height: 23vh;
  margin-top: 1.5vh;
  margin-left: 1vw;
  margin-right: 1vw;
  border-radius: 3vh;

}

.weather-overlay4{
  background: white;
  width: 100%;
  height: 100%;
}

.weather-overlay3 p {
  text-align: center;
  color: #f17109;
  font-weight: bold;

}

.weather-overlay3 h1{
  text-align: center;
  color: white;
  margin-top: 1vh;
  border: 0.2vh solid white;
  border-radius: 2vh;

}

.weather-data-Icon{
  width: 5vw;
  height: 8vh;
  margin-top:1vh;
  border-bottom: 0.1vh solid white;

}

.weather-overlay3 h5{
  text-align: center;
  color: white;
  padding-top: 0.5vh;
}


.weather-icon{
  grid-row: 2/5;
  grid-column: 2/5;
}

.weather-icon img{
  width: 5vw;
  height: 6vh;
}


.weather-location{
  grid-row: 3/8;
  grid-column: 2/11;
  font-size: 2.2vh;
  /*border: 2px solid red;*/
}

.w-temperature{
  grid-row: 7/16;
  grid-column: 2/6;
  font-size: 8vh;
}

.w-temperature p{
  position: relative;
  bottom: 2vh;
}

.w-degrees{
  grid-row: 9/11;
  grid-column: 6/7;
  position: relative;
  right: 0.7vw;
  bottom: 1vh;

}

.w-max{
  grid-row: 9/14;
  grid-column: 8/10;
  position: relative;
  left: 0.5vw;
  border-bottom: 0.1vh solid white;
  font-size: 2vh;
  font-weight: 200;
}


.w-min{
  grid-row: 14/19;
  grid-column:8/10;
  position: relative;
  left: 0.65vw;
  font-size: 2vh;

}



.w-degrees img{
  width: 1.5vw;
  height: 2vh;
}


.w-wind-icon{
  grid-row: 3/11;
  grid-column: 13/16;
  position: relative;
  right: 1vh;
}

.w-wind-icon img{
  width: 3vw;
  height: 5vh;
}

.w-wind-gust{
  grid-column: 16/19;
  border-bottom: 0.1vh solid white;
  position: relative;
  top: 0.5vh;
  bottom: 0.2vh;
  right: 0.5vw;
  grid-row: 3/6;
  font-weight: 100;

}

.w-wind-gust p{
  position: relative;
  bottom: 0.5vh;
  font-weight: 400;
  font-size: 1.4vh;

}

.wind-speed{
  position: relative;
  top: 0.8vh;
  right: 0.7vh;
  grid-row: 6/9;
  grid-column: 16/20;
  font-size: 1.4vh;
}

.weather-time{
  grid-row: 12/21;
  grid-column:13/20;
  font-weight: 400;
  position: relative;
  right: 0.5vw;
}

.weather-grid{
  display: grid;
  grid-template-rows: repeat(20, 1fr);
  grid-template-columns: repeat(20, 1fr);
  height: 100%;
  width: 100%;
}

.temp{
  border: 2px solid red;
  grid-row: 1/9;
  grid-column: 1/11;
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(10, 1fr);
  height: 100%;
  width: 100%;
}

.weather-date{
  border: 2px solid blue;
  grid-row:1/3;
  grid-column: 1/11;
  text-align: center;
  font-size: 3vh;
}

.weather-desc{
  border: 2px solid blue;
  grid-row:3/6;
  grid-column: 1/11;
}

.temperature{
  border: 2px solid blue;
  grid-row: 6/11;
  grid-column: 1/11;
}


.restOfDay{
  border: 2px solid red;
  grid-column: 1/21;
  grid-row: 9/14;
}
.location{
  border: 2px solid red;
  grid-row: 14/17;
  grid-column: 1/21;
  text-align: center;
  font-size: 6vh;
}
.Mainicon{
  border: 2px solid red;
  grid-row: 1/9;
  grid-column: 11/21;
}

















.weather-wave{
  grid-row:10/21;
  grid-column: 1/21;
}

.weather-wave img{
  height: 100%;
  width: 100%;
}






</style>