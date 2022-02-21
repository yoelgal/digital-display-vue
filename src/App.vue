<template>
  <div id="app">
    <div class="grid-container">
      <fixtures class="bg"></fixtures>
      <school-notices class="bg"></school-notices>
      <department-notices class="bg"></department-notices>
      <news class="bg"></news>
      <weather class="bg"></weather>
      <bus class="bg"></bus>
      <room-uses class="bg"></room-uses>
      <lunch class="bg"></lunch>
      <date-time-dad-joke class="bg"></date-time-dad-joke>
    </div>
  </div>
</template>
<script>
import Bus from './components/Bus.vue'
import SchoolNotices from "@/components/School-notices";
import news from "@/components/News";
import departmentNotices from "@/components/Department-notices";
import weather from "@/components/Weather";
import roomUses from "@/components/Room-uses";
import lunch from "@/components/Lunch";
import dateTimeDadJoke from "@/components/Date-time-Dad-joke";
import fixtures from "@/components/Fixtures";

export default {
  name: 'App',
  components: {
    Bus,
    fixtures,
    news,
    SchoolNotices,
    departmentNotices,
    weather,
    roomUses,
    lunch,
    dateTimeDadJoke,

  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Oswald');
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300&family=Kanit:wght@300&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Dongle:wght@300&family=Kanit:wght@300&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
@import url('https://fonts.googleapis.com/css2?family=Rowdies&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;


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

.grid-container::before{
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width:100%;
  height: 100%;
  background: linear-gradient( to bottom,#af0808, #9a609a);
  opacity: 0.5;
  clip-path: circle(30% at right 70%);

}

.grid-container::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(#e91e63,#2196f3 );
  clip-path: circle(20% at 10% 100%);
  /*clip-path: circle(20% at 50% 0%);*/
  opacity: 0.5;
}

.grid-container {
  display: grid;
  /*grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;*/
  /*grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;*/
  grid-template-columns: repeat(30, 1fr);
  grid-template-rows: repeat(30, 1fr);
  gap: 2.5vh;
  padding: 3vh;
  height: 100vh;
  background-color: #272748;
  /*background-color: #e70404;*/
}

.grid-container > div {
  z-index: 1;
  background: rgba(206, 182, 182, 0.1);
  box-shadow: 1vh 1vh 3vh rgba(0, 0, 0, 0.5);
  border-radius: 2vh;
  border-top: 0.2vh solid rgba(255, 255, 255, 0.5);
  border-left: 0.2vh solid rgba(255, 255, 255, 0.5);
  backdrop-filter: blur(0.5vh);
}

.bg {
  z-index: 1;
  background: rgba(206, 182, 182, 0.1);
  box-shadow: 1vh 1vh 3vh rgba(0, 0, 0, 0.5);
  border-radius: 2vh;
  border-top: 0.2vh solid rgba(255, 255, 255, 0.5);
  border-left: 0.2vh solid rgba(255, 255, 255, 0.5);
  backdrop-filter: blur(0.5vh);

}
</style>
