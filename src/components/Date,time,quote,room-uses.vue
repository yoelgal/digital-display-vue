<template>
  <div class="date-time">
    <div class="date-overlay1 border-blue-shadow">
      <h1>{{ hours}}:{{ mins }}:{{secs}}</h1>
      <div class="date-line1"></div>
      <h2>{{ day }} {{ date }} {{ month }}</h2>
      <div class="date-clock-icon">

      </div>

    </div>
    <div class="date-overlay2">
      <div class="quote-container">
        <div>Daily Quote 📔</div>
        <i class="quote-text">“I have always known what I wanted, and that was beauty… in every form.”. – Joan Crawford.</i>
      </div>
    </div>
    <div class="date-overlay3 border-blue">
      <div style="position: absolute;top: 1vh; opacity: 0.2;filter: blur(0.3vh); left: 3vw;width: 4vw;height: 6vh" class="ellipse"></div>
      <div style="position: absolute;top: 20vh; opacity: 0.2;filter: blur(0.3vh); left: 12vw;width: 6vw;height: 9vh" class="ellipse"></div>
      <div class="int-times">
        <div><span class="nyc">NYC</span>  00:00 </div>
        <div><span class="syd">SYD</span>  00:00 </div>
        <div><span class="tky">TKY</span>  00:00 </div>
      </div>
    </div>
  </div>

<!--      <div class="int-times">-->
<!--          <div><span class="nyc">NYC</span>  00:00:00 🗽</div>-->
<!--          <div><span class="syd">SYD</span>  00:00:00 🦘</div>-->
<!--          <div><span class="jpn">JPN</span>  00:00:00 🗾</div>-->
<!--      </div>-->
<!--     <div class="room-title">-->
<!--        <h1>Room Uses 🗓</h1>-->
<!--      </div>-->
<!--        <div class="room-box">-->
<!--          <div class="room-container1">-->
<!--            <h1>IT 1:</h1>-->
<!--            <h1>...</h1>-->
<!--          </div>-->
<!--          <div class="room-container2">-->
<!--            <h1>IT 2:</h1>-->
<!--            <h1>...</h1>-->
<!--          </div>-->
<!--          <div class="room-container3">-->
<!--            <h1>IT 3:</h1>-->
<!--            <h1>...</h1>-->
<!--          </div>-->
<!--          <div class="room-container4">-->
<!--            <h1>IT 4:</h1>-->
<!--            <h1>...</h1>-->
<!--          </div>-->
<!--        </div>-->


<!--     <div class="quote">-->
<!--       <div>Daily Quote </div>-->
<!--       <i>filler text filler text here is some more filler text</i>-->
<!--     </div>-->

<!--    </div>-->
<!--    <div class="date-overlay3"></div>-->
<!--    <div class="date-overlay4">-->
<!--      <div class="int-times">-->
<!--        <div>NYC: 00:00:00 🇺🇸</div>-->
<!--        <div>SYD: 00:00:00 🇦🇺</div>-->
<!--        <div>JPN: 00:00:00 🇯🇵</div>-->
<!--      </div>-->


<!--    <div class="date-overlay5 border-blue">-->
<!--      <div class="date-ellipse1"></div>-->
<!--&lt;!&ndash;      <quote></quote>&ndash;&gt;-->
<!--    </div>-->

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
  box-shadow: 0vh 0vh 0.1vh 0.7vh #1d94d9, 0vh 0vh 0.1vh 1.5vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}

.border-blue-shadow{
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed, 0vh 0vh 3vh 2vh #1e1d1d;

}

.ellipse{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 3vw;
  height: 5vh;


}

.date-time {
  grid-column: 12/24;
  grid-row: 10/22;
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
  grid-column: 1/7;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;*/
  border-bottom-left-radius: 2vh;
  border-bottom-right-radius: 2vh;
  display: flex;
  flex-direction: column;
  background: #2a2828;
  overflow: hidden;
  position: relative;
  right: 4vw;
  width: 25vw;

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
  width: 70%;
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
  border-radius: 2vh;
  background: #2a2828;
}

.quote-container{
  position: relative;
  top: 21vh;
  left: 1vw;
  width: 20vw;

}

.quote-container div:nth-child(1){
  font-size: 3vh;

}

.quote-container i {
  font-size: 1.5vh;
  font-weight: 400;
}

.date-overlay3{
  background: #2a2828;
  grid-row: 2/10;
  grid-column: 7/11;
  position: relative;
  /*box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #2196f3,0vh 0vh 0.1vh 1.6vh #1c3da8;*/
  border-bottom-left-radius: 10vh;
  border-top-left-radius: 10vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}


.int-times{
  position: relative;
  left: 3vw;
  top: -2vh;
  display: flex;
  flex-direction: column;
}

.int-times div{
  font-size: 3.5vh;
  margin-top: 4vh;
}

.int-times span{
  font-size: 1.5vh;
}



/*.room-title h1 {*/
/*  font-size: 3vh;*/
/*  font-weight: 500;*/
/*  position: relative;*/
/*  top: 19vh;*/
/*  left: 1.5vw;*/
/*}*/

/*.room-box{*/
/*  position: relative;*/
/*  top: 20vh;*/
/*  left: 0.5vw;*/
/*  width: 26vw;*/
/*  height: 20vh;*/
/*  display: flex;*/
/*  flex-direction: row;*/
/*  justify-content: space-evenly;*/
/*}*/

/*.room-box h1{*/
/*  font-size: 3vh;*/
/*}*/

/*.room-container1 {*/
/*  width: 5vw;*/
/*  height: 13vh;*/
/*  border: 0.2vh solid white;*/
/*  border-radius: 2vh;*/
/*  text-align: center;*/
/*}*/




/*.room-container2 {*/
/*  width: 5vw;*/
/*  height: 13vh;*/
/*  border: 0.2vh solid white;*/
/*  border-radius: 2vh;*/
/*  text-align: center;*/
/*}*/

/*.room-container3 {*/
/*  width: 5vw;*/
/*  height: 13vh;*/
/*  border: 0.2vh solid white;*/
/*  border-radius: 2vh;*/
/*  text-align: center;*/
/*}*/

/*.room-container4 {*/
/*  width: 5vw;*/
/*  height: 13vh;*/
/*  border: 0.2vh solid white;*/
/*  border-radius: 2vh;*/
/*  text-align: center;*/
/*}*/



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