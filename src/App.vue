<template>
  <div id="app">
    <div class="grid-container">
      <Title></Title>
      <school-notices></school-notices>
      <department-notices></department-notices>
      <period></period>
      <weather></weather>
      <bus></bus>
      <room-uses></room-uses>
      <facts></facts>
      <lunch></lunch>
      <date-time-dad-joke></date-time-dad-joke>
    </div>
  </div>
</template>

<script>
import Bus from './components/Bus.vue'
import Title from './components/Title'
import SchoolNotices from "@/components/School-notices";
import departmentNotices from "@/components/Department-notices";
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
  background: rgb(56, 52, 52);
  padding: 3vh;
  height: 100vh;
}

.grid-container > div {
  padding: 0vh;
  color: white;
  border-radius: 2vh;
  background: #444343de;
   /*box-shadow: 0.2vh 0.2vh 0.1vh #f10842, 0.5vh 0.5vh 1vh #4e4b4b,
    -0.4vh -0.4vh 0.1vh #12cbd8, -0.5vh -0.5vh 0.1vh #ffffff;*/
  /* 5px 5px 10px #4e4b4b,
             -5px -5px 10px #ffffff; */
  display: flex;
  box-shadow: 0.5vh 0.5vh 0.5vh black, -0vh 0vh 0.1vh #1f1c1c,
  inset 0.2vh 0.2vh 0.1vh black, inset -0vh -0vh 0.1vh #111010;
}
</style>
