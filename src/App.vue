<template>
  <div id="app">
    <div class="grid-container">
      <Title class="bg"></Title>
      <school-notices class="bg"></school-notices>
      <department-notices class="bg"></department-notices>
      <period class="bg"></period>
      <weather class="bg"></weather>
      <bus class="bg"></bus>
      <room-uses class="bg"></room-uses>
      <facts class="bg"></facts>
      <lunch class="bg"></lunch>
      <date-time-dad-joke class="bg"></date-time-dad-joke>
    </div>
  </div>
</template>

<script>
import Bus from './components/Bus.vue'
import Title from './components/Title'
import SchoolNotices from "@/components/School-notices";
import departmentNotices from "@/components/News";
import period from "@/components/Period";
import weather from "@/components/Weather";
import roomUses from "@/components/Room-uses";
import facts from "@/components/Quote";
import lunch from "@/components/Lunch";
import dateTimeDadJoke from "@/components/Date-time-Dad-joke";

export default {
  name: 'App',
  components: {
    Bus,
    Title,
    SchoolNotices,
    departmentNotices,
    period,
    weather,
    roomUses,
    facts,
    lunch,
    dateTimeDadJoke
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Oswald');
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300&family=Kanit:wght@300&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;

  color: whitesmoke;

}

#app {
  /*
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  */
}

.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  gap: 2vh;
  padding: 3vh;
  height: 100vh;
  background-color: #7491ad;
  /*background-color: #e70404;*/
}

.grid-container > div {
  padding: 0vh;
  color: white;
  border-radius: 2vh;
  /*background: #444343de;*/
   /*box-shadow: 0.2vh 0.2vh 0.1vh #f10842, 0.5vh 0.5vh 1vh #4e4b4b,
    -0.4vh -0.4vh 0.1vh #12cbd8, -0.5vh -0.5vh 0.1vh #ffffff;*/
  /* 5px 5px 10px #4e4b4b,
             -5px -5px 10px #ffffff; */
  display: flex;
  box-shadow: 0.5vh 0.5vh 0.5vh black, -0vh 0vh 0.1vh #1f1c1c,
  inset 0.2vh 0.2vh 0.1vh black, inset -0vh -0vh 0.1vh #111010;
}

.bg {
  background-color: #273c75;
}
</style>
