<template>
  <div class="date-time">
    <div class="date-overlay1 border-blue">
      <h1>{{ hours}}:{{ mins }}:{{ secs }}</h1>
      <div class="date-line1"></div>
      <h2>{{ day }} {{ date }} {{ month }}</h2>
      <div class="date-clock-icon">

      </div>

    </div>
    <div class="date-overlay2 border-blue">
      <div class="room-title">
        <h1>Room Uses 🗓</h1>
      </div>
      <div class="room-container1">
        <h1>IT 1:</h1>
        <h1>...</h1>
      </div>
      <div class="room-container2">
        <h1>IT 2:</h1>
        <h1>...</h1>
      </div>
      <div class="room-container3">
        <h1>IT 3:</h1>
        <h1>...</h1>
      </div>
      <div class="room-container4">
        <h1>IT 4:</h1>
        <h1>...</h1>
      </div>
      <div class="date-line2"></div>
     <div class="quote">
       <div>Daily Quote </div>
       <i>filler text filler text here is some more filler text</i>
     </div>

    </div>
    <div class="date-overlay3"></div>
    <div class="date-overlay4">
      <div class="int-times">
        <div>NYC: 00:00:00 🇺🇸</div>
        <div>SYD: 00:00:00 🇦🇺</div>
        <div>JPN: 00:00:00 🇯🇵</div>
      </div>

    </div>
<!--    <div class="date-overlay5 border-blue">-->
<!--      <div class="date-ellipse1"></div>-->
<!--&lt;!&ndash;      <quote></quote>&ndash;&gt;-->
<!--    </div>-->
  </div>
</template>

<script>
// import quote from "@/components/Quote";

export default {
  name: "Date-time",
  components: {
    // quote
  },
  data() {
    return {
      days: ["SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"],
      months: ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"],
      polling: null,
      hours: "00",
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
            this.hours = date.getHours().toString().padStart(2, '0')
            this.mins = date.getMinutes().toString().padStart(2, '0')
            this.secs = date.getSeconds().toString().padStart(2, '0')

            this.day = this.days[date.getDay()]
            this.date = date.getDate()
            this.month = this.months[date.getMonth()]
          }, 1000)
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
.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}

.date-time {
  grid-column: 12/24;
  grid-row: 17/31;
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: repeat(10, 1fr);
  overflow: hidden;
  color: white;
}


.date-ellipse1 {
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 10vw;
}


.date-overlay1 {
  grid-row: 1/5;
  height: 18vh;
  grid-column: 1/8;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;*/
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  display: flex;
  flex-direction: column;
  background: #2a2828;
  overflow: hidden;
  position: relative;
  right: 4vw;

}

.date-overlay1 h1 {
  font-size: 8.2vh;
  position: relative;
  left: 4.5vw;
}

.date-line1 {
  position: relative;
  left: 4.5vw;
  bottom: 1vh;
  background-color: white;
  width: 80%;
  height: 0.3vh;
  border-radius: 2vh;
}



.date-overlay1 h2 {
  font-size: 3vh;
  position: relative;
  left: 4.5vw;

}

.date-overlay2 {
  z-index: -2;
  grid-row: 1/11;
  grid-column: 1/12;
  position: relative;
  right: 0.9vw;
  border-radius: 2vh;
  background: #2a2828;


}

.room-title h1 {
  font-size: 3vh;
  font-weight: 500;
  position: relative;
  top: 21vh;
  left: 1.5vw;
}

.room-container1 {
  width: 5vw;
  height: 11vh;
  position: relative;
  top: 22vh;
  left: 1.5vw;
  border: 0.2vh solid white;
  border-radius: 2vh;
  text-align: center;
}




.room-container2 {
  width: 5vw;
  height: 11vh;
  position: relative;
  top: 11vh;
  left: 7.5vw;
  border: 0.2vh solid white;
  border-radius: 2vh;
  text-align: center;
}

.room-container3 {
  width: 5vw;
  height: 11vh;
  position: relative;
  bottom: 0vh;
  left: 13.5vw;
  border: 0.2vh solid white;
  border-radius: 2vh;
  text-align: center;
}

.room-container4 {
  width: 5vw;
  height: 11vh;
  position: relative;
  bottom: 11vh;
  left: 19.5vw;
  border: 0.2vh solid white;
  border-radius: 2vh;
  text-align: center;
}

.quote{
  position: relative;
  left: 24.5vw;
  bottom: 47vh;
  width: 11vw;
}
.quote div{
  font-size: 3vh;
  width: 13vw;
  position: relative;
  left: 1vw;
  text-decoration: underline;
}

.quote i{
  position: relative;
  left: 1vw;
  font-size: 1.4vh;
  font-weight: 300;
}
.int-times{
  text-align: center;
  width: 10vw;
  height: 20vh;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  font-size: 2vh;

}

.int-times div{
  position: relative;
  left: 0.5vw;
}


.date-overlay4{
  background: #2a2828;
  box-shadow: 0vh 0vh 0.1vh 0.7vh #2196f3,0vh 0vh 0.1vh 1.6vh #4c2bed;
  grid-row: 4/11;
  position: relative;
  top: 8vh;
  grid-column: 8/12;
  border-top-right-radius: 2vh;
  border-top-left-radius: 2vh;
}

</style>