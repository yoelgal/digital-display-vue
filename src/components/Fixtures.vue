<template>
  <div class="fixtures">
    <div class="fixtures-overlay1 border-blue">
      <div class="fixture-container">
        <div class="ellipse1"></div>
        <div>Sport Fixtures 🏅</div>
        <!--I assume emoji can be changed depending one sport-->
        <div class="sport"><span style="position:relative;top: 2vh;overflow: hidden">{{fixtures[position].emoji}}</span>️</div>
        <div class="team"><span style="opacity: 0.5;font-weight: 200">Team: </span><span
            style="display: block;font-size: 2vh">{{ fixtures[position].team }}</span></div>
        <div class="line"></div>
        <div class="date">{{ fixtures[position].dateFormat }}</div>
        <div class="opposition"><span style="opacity: 0.5;font-weight: 200">Opposition: </span><span
            style="display: block;font-size:2vh;width: 20vw;">{{ fixtures[position].opponent }}</span></div>
      </div>
    </div>
    <div class="fixtures-overlay2 border-blue">
      <div class="key-dates-container">
        <div class="ellipse2"></div>
        <div>Key Dates 🗓</div>
        <div></div>
      </div>

    </div>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Fixtures",
  data() {
    return {
      polling: null,
      position: 0,
      fixtures: []

    }
  },
  methods: {
    pullData() {
      axios.get('https://fathomless-crag-41517.herokuapp.com/fixtures').then(response=>(this.fixtures = response.data))
    },
    getPos() {
      this.polling = setInterval(()=>{
        this.position >= this.fixtures.length ? this.position = 0 : this.position += 1
      }, 4000)
    }
  },
  mounted() {
    this.pullData()
  },
  beforeDestroy() {
    clearInterval(this.polling)
  },
  created() {
    this.getPos()
  }
}
</script>

<style scoped>


.border-blue {
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0 0 0.1vh 0.5vh #1d94d9, 0 0 0.1vh 1vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}

/*.ellipse1{*/
/*  !*background: linear-gradient(#1ccece, #2072d0);*!*/
/*  border-radius: 50%;*/
/*  border-left: 0.6vh solid #2196f3;*/
/*  width: 5vw;*/
/*  height: 10vh;*/
/*  position: absolute;*/
/*  left: 13vw;*/
/*  top: 5vh;*/

/*}*/
/*.ellipse2{*/
/*  !*background: linear-gradient(#1ccece, #2072d0);*!*/
/*  border-radius: 50%;*/
/*  border: 0.2vh solid white;*/
/*  width: 3vw;*/
/*  height: 5vh;*/
/*  position: absolute;*/
/*  left: 9.5vw;*/
/*  top: 17vh;*/
/*}*/

.fixtures {
  grid-row: 22/31;
  grid-column: 12/24;
  background-color: #2a2828;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(12, 1fr);
  overflow: hidden;
  color: white;
}

/*which sport,  date, team, opponent*/
.fixtures-overlay1 {
  grid-row: 1/13;
  grid-column: 1/8;
  border-bottom-right-radius: 2vh;
  border-top-right-radius: 2vh;
  position: relative;
  right: 1vw;
  overflow: hidden;

}

.fixtures-overlay2 {
  grid-row: 1/13;
  grid-column: 9/13;
  border-bottom-left-radius: 2vh;
  border-top-left-radius: 2vh;
}

.fixture-container {
  position: relative;
  left: 1.3vw;
  top: 1vh;
  font-size: 3vh;
  width: 14.5vw;
  height: 18vh;

}


.date {
  font-size: 2vh;
  position: relative;
  left: 7vw;
  bottom: 5.5vh;
  font-weight: 300;
}

.line {
  height: 0.1vh;
  width: 12vw;
  background: white;
  position: relative;
  top: 1.5vh;
}

.sport {
  position: absolute;
  left: 14vw;
  bottom: 3vh;
  font-size: 10vh;
}

.team {
  font-size: 1.5vh;
  position: relative;
  top: 1vh;

}

.opposition {
  font-size: 1.5vh;
  position: relative;
  top: 0vh;
}


.key-dates-container {
  position: relative;
  left: 1vw;
  top: 1vh;
  font-size: 3vh;
  width: 12vw;
  height: 18vh;
}


</style>