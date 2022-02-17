<template>
  <div class="date-time">
    <div class="date-overlay1">
      <h1>10:17:00</h1>
      <div class="date-line1"></div>
      <h2>📅 THU 17 FEB</h2>
      <div class="date-clock-icon">
        <img src='../assets/3Dclock.png'>
      </div>

    </div>
    <div class="date-overlay2">
      <div class="room-title">
        <h1>Room Uses 🗓</h1>
      </div>
      <div class="room-container1">
        <h1>IT 1:</h1>
        <h1>10C</h1>
      </div>
      <div class="room-container2">
        <h1>IT 1:</h1>
        <h1>10C</h1>
      </div>
      <div class="room-container3">
        <h1>IT 1:</h1>
        <h1>10C</h1>
      </div>
      <div class="room-container4">
        <h1>IT 1:</h1>
        <h1>10C</h1>
      </div>
      <div class="date-line2"></div>
      <div class="quote-title-container">
        <h1>📖 Daily Quote</h1>
      </div>
      <div class="quote-container">
        <p>here is some more filler text. I am starting to like webstorm a bit more.</p>
      </div>
    </div>
    <div class="date-overlay3"></div>
    <div class="date-overlay4">

    </div>
    <div class="date-overlay5">
      <div class="dad-joke-title">
        <h1>Dad Joke 😆</h1>
      </div>
      <div class="dad-joke-container">
        <p>for some reason i can't get filler text on webstorm so I am writing this instead.</p>
      </div>
    </div>
<!--    <div class="date-time-grid">-->
<!--      <div class='date-time-line1-container'>-->
<!--        <div class='date-time-line1'></div>-->
<!--      </div>-->
<!--      <div class="time">-->
<!--        <p>{{ hours.local }}:{{ mins }}:{{ secs }}</p>-->
<!--      </div>-->
<!--      <dad-joke></dad-joke>-->
<!--      <div class="date">-->
<!--        <h1>{{ day }}</h1>-->
<!--        <br/>-->
<!--        <h1>{{ date }}</h1>-->
<!--        <br/>-->
<!--        <h1>{{ month }}</h1>-->
<!--      </div>-->
<!--      <div class="international-times">-->
<!--        <div>-->
<!--          <div style="font-size: 3vh; text-align: center;text-decoration: underline;">NYC</div>-->
<!--          <div>{{ hours.NYC }}:{{ mins }}</div>-->
<!--        </div>-->
<!--        <div>-->
<!--          <div style="font-size: 3vh;text-align: center;text-decoration: underline;">SYD</div>-->
<!--          <div>{{ hours.SYD }}:{{ mins }}</div>-->
<!--        </div>-->
<!--        <div>-->
<!--          <div style="font-size: 3vh;text-align: center;text-decoration: underline;">TKY</div>-->
<!--          <div>{{ hours.TKY }}:{{ mins }}</div>-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->
  </div>
</template>

<script>
// import dadJoke from "@/components/Dad-joke";

export default {
  name: "Date-time",
  components: {
    // dadJoke
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
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: repeat(10, 1fr);
  overflow: hidden;
  color: white;
}


.date-overlay1{
  grid-row: 1/4;
  grid-column: 1/9;
  background: #dc4b4b;
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  display: flex;
  flex-direction: column;

}

.date-overlay1 h1{
  font-size: 8.2vh;
  position: relative;
  left: 1vw;
}

.date-line1{
  position: relative;
  left: 0.5vw;
  bottom: 1vh;
  border: 0.2vh solid #090808;
  width: 70%;
  height: 0.1vh;
}

.date-clock-icon{
  position: relative;
  left: 13.4vw;
  width: 5vw;
  bottom: 4.4vh;
  height: 4vh;
}


.date-clock-icon img{
  width: 5vw;
  height: 8vh;
  position: relative;
  bottom: 3vh;
  left: 1.5vw;
}

.date-overlay1 h2{
  font-size: 3vh;
  position: relative;
  left: 1vw;

}

.date-overlay2{
  z-index:-2;
  grid-row: 1/11;
  grid-column: 1/11;
  position: relative;
  right: 1vw;
  background: #dc4b4b;
  border-radius: 2vh;
  box-shadow: 0vh 0vh 0.1vh 0.7vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;
}

.room-title h1{
  font-size: 4vh;
  position: relative;
  top: 20vh;
  left: 2vw;
}

.room-container1 {
  width: 5vw;
  height: 10vh;
  position: relative;
  top: 20vh;
  left: 1.5vw;
  border: 0.2vh solid white;
  border-radius: 2vh;
  text-align: center;
}
.room-container2 {
  width: 5vw;
  height: 10vh;
  position: relative;
  top: 10vh;
  left: 7.5vw;
  border: 0.2vh solid white;
  border-radius: 2vh;
  text-align: center;
}
.room-container3 {
   width: 5vw;
   height: 10vh;
   position: relative;
   top: 0vh;
   left: 13.5vw;
   border: 0.2vh solid white;
   border-radius: 2vh;
   text-align: center;
 }
.room-container4 {
    width: 5vw;
    height: 10vh;
    position: relative;
    bottom: 10vh;
    left: 19.5vw;
    border: 0.2vh solid white;
    border-radius: 2vh;
    text-align: center;
}
.date-line2{
  border: 0.2vh solid #090808;
  width: 90%;
  height: 0.1vh;
  position: relative;
  left: 1.5vw;
  bottom: 9vh;
}

.quote-title-container{
  width: 13vw;
  height: 7vh;
  position: relative;
  left: 11.5vw;
  bottom: 8vh;
  font-size: 1.5vh;
}

.quote-container{
  width: 7vw;
  height: 16vh;
  position: relative;
  left: 17.5vw;
  bottom: 10vh;
  font-weight: 400;
}

.date-overlay3{

}
/*.date-overlay4{*/
/*  background: #dc4b4b;*/
/*  box-shadow: 0vh 0vh 0.1vh 0.7vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;*/
/*  grid-row: 5/8;*/
/*  position: relative;*/
/*  top: 5vh;*/
/*  grid-column: 1/6;*/
/*  border-top-right-radius: 100%;*/
/*  z-index: -3;*/
/*}*/

.date-overlay4 h1{
  position: relative;
  top: 1.5vh;
  left: 0.5vw;
}

.date-overlay4 h1:nth-child(2){
  position: relative;
  left: 2.5vw;
}

.date-overlay5{
  position: relative;
  top: 4vh;
  grid-row: 7/11;
  grid-column: 1/7;
  background: #dc4b4b;
  box-shadow: 0vh 0vh 0.1vh 0.7vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;
  border-top-right-radius: 80%;
  display:flex;
  flex-direction: column;
  justify-content: left;
  overflow: hidden;
}

.dad-joke-title{
  height: 7vh;
  width: 8vw;
  position: relative;
  top: 0.5vh;
  left: 0.5vw;
}

.dad-joke-title h1{
  padding-left: 0.5vw;
}

.dad-joke-container{
  position: relative;
  top: 3vh;
  left: 0.5vw;
  max-width: 12vw;
  height: 8vh;
}

.dad-joke-container p{
  padding-left: 0.5vw;
  font-weight: 400;
}




</style>