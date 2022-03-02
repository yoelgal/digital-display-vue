<template>
  <div class="news">
    <div class='news-grid'>
      <div class="news-ellipse1"></div>
      <div class="news-ellipse2"></div>
      <div class="news-icon">
        <img src='../assets/perspective__matte.png'>
      </div>
      <div class="news-overlay border-blue-shadow">
        <div class="news-title">
          Daily News
        </div>
        <div  class="news-underline1"></div>
        <div class="newsDate">
          <p>{{ day }} {{ date }} {{ month }}</p>
        </div>
        <div class="topStories">Top Stories</div>


      </div>
      <div class="news-data border-blue-shadow">
        <div class="news-data1">
          <div class="news-acc-data">
            <p>{{ polledData[startNum].title }} - {{polledData[startNum].source}}</p>
          </div>
          <div class="news-ellipse3"></div>
          <div class="news-ellipse4"></div>

        </div>
      </div>
      <div class="news-overlay2 border-blue">
        <div class="news-ellipse5"></div>
        <div class="news-ellipse6"></div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Department-notices",
  data() {
    return {
      days: ["SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"],
      months: ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"],
      day: "day...",
      date: "number...",
      month: "month...",
      polling: null,
      startNum: 0,
      polledData: ['loading...', 'loading...', 'loading...'],
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const news = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/news')).json());
        this.polledData = news
        this.startNum >= this.polledData.length ? this.startNum = 0 : this.startNum+=1
      }, 10000)
    },
    pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/news')
          .then(response => (this.polledData = response.data))
    }
  },
  mounted() {
    this.pullData()
    const date = new Date()
    this.day = this.days[date.getDay()]
    this.date = date.getDate()
    this.month = this.months[date.getMonth()]
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
.border-blue{
  /*box-shadow: 0.2vh 0.2vh 2.5vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;*/
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed;
  /*box-shadow: 0.2vh 0.2vh 0.3vh 0.6vh #7dc5ef,  0.2vh 0.2vh 0.7vh 0.6vh #4587e4,  0.2vh 0.2vh 1vh 0.6vh #0861ef*/

}

.border-blue-shadow{
  box-shadow: 0.2vh 0.2vh 0.1vh 0.5vh #1d94d9, 0.5vh 0.3vh 0.1vh 1vh #4c2bed, 0vh 0vh 3vh 2vh #1e1d1d;

}

.news-ellipse1{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 0.9vw;
  height: 1.4vh;
  position: absolute;
  left: 7vw;
  top: 1vh;
}

.news-ellipse2{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 0.6vw;
  height: 1vh;
  position: absolute;
  left: 8vw;
  top: 3vh;
}


.news {
  grid-column: 22/31;
  grid-row: 1/10;
  overflow: hidden;
  color: white;
}

.news-grid {
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(13, 1fr);
  width: 100%;
  height: 100%;
}

.news-overlay{
  grid-row: 1/11;
  grid-column: 1/6;
  border-bottom-right-radius: 3vh;
  border-top-right-radius: 3vh;
  background: #2a2828;
}

.news-title{
  font-size: 3vh;
  padding-top: 1vh;
  padding-left: 0.3vw;
  grid-row: 1/3;
  width:5vw;
}

.news-icon{
  grid-row: 7/8;
  margin-top: 5vh;
  grid-column: 4/11;
  z-index: 1;
}

.news-icon img{
  width: 3vw;
  height: 5vh;
}


.news-underline1{
  border: 0.08vh solid grey;
  width: 100%;
  height: 0.1vh;

}
.newsDate{
   font-size:1.5vh;
   grid-row: 3/5;
   grid-column: 1/3;
   display: flex;
   align-content: flex-start
}

.newsDate p {
  font-weight: 200;
  margin-left: 0.2vw;
  padding-top: 1vh;

}

.topStories{
  margin-left: 0.2vw;
  margin-top: 1vh;
  font-size: 4vh;
  background-image: -webkit-gradient( linear, left top, right top, color-stop(0.40, #73a7e3), color-stop(0.10, #1fc9c9), color-stop(0.80, #0992dc));
  /*background-image: gradient( linear, left top, right top, color-stop(0.20, #1ccece), color-stop(0.15, #2072d0), color-stop(0.3, #22f));*/
  color:transparent;
  -webkit-background-clip: text;
  font-weight: 600;
  /*background: linear-gradient(#1ccece, #2072d0);*/
  /*-webkit-text-stroke-color: white;*/
  /*-webkit-text-stroke-width: 0.1vh;*/
}

.topStories::first-line{
  color: white;
}

.news-data{
  grid-row: 1/8;
  grid-column: 4/13;
  position: relative;
  left: 1.3vw;
  border-top-right-radius: 1vh;
  display: grid;
  grid-template-rows: repeat(20, 1fr);
  grid-template-columns: repeat(20, 1fr);
  z-index:-1;
  border-bottom-right-radius: 2vh;
  background: #2a2828;


}


.news-data1{
  grid-row: 2/17;
  grid-column: 5/20;
  border-radius: 2vh;

  /*box-shadow: inset 0.2vh 0.2vh 0.2vh #2196f3,*/
  /*inset -0.2vh -0.2vh 0.2vh #2196f3;*/

}

/*#949494*/

.news-acc-data{
  width: 100%;
  height: 90%;
  position:relative;
  top: 10%;
}

.news-acc-data p {
  color: white;
  padding-left: 0.5vw;
  padding-right: 0.5vw;
  font-size: 1.6vh;
}

.news-ellipse3{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 0.7vw;
  height: 1vh;
  position: absolute;
  left:17vw;
  top: 19.5vh;
}

.news-ellipse4{
  background: linear-gradient(#1ccece, #2072d0);
  border-radius: 50%;
  width: 0.9vw;
  height: 1.4vh;
  position: absolute;
  left: 18vw;
  top: 18vh;

}

.news-wave {

  margin-top: 2vh;
  height: 4vh;
}

.news-wave img{
  height: 100%;
  width: 100%;
}

.news-overlay2{
  background: #2a2828;
  grid-row: 1/11;
  grid-column: 1/14;
  z-index: -2;
  position: relative;
  top: 2vh;
  left: 2vw;
  border-bottom-right-radius: 2vh;
}

/*.news-ellipse5{*/
/*  background: linear-gradient(#1ccece, #2072d0);*/
/*  border-radius: 50%;*/
/*  width: 0.9vw;*/
/*  height: 1.4vh;*/
/*  position: relative;*/
/*  left:10vw;*/
/*  top: 21vh;*/

/*}*/
/*.news-ellipse6{*/
/*  background: linear-gradient(#1ccece, #2072d0);*/
/*  border-radius: 50%;*/
/*  width: 0.9vw;*/
/*  height: 1.4vh;*/
/*  position: relative;*/
/*  left: 24vw;*/
/*  top: 20.5vh;*/
/*}*/


/*.news-underline2{*/
/*  position: relative;*/
/*  border-radius:2vh;*/
/*  height:0.5vh;*/
/*  background-color: #2196f3;*/
/*  box-shadow: 0vh 0.2vh 0.3vh #d51c57;*/

/*}*/

/*.news-underline3{*/
/*  position: relative;*/
/*  top: 2vh;*/
/*  border-radius:2vh;*/
/*  height:0.5vh;*/
/*  background-color: #2196f3;*/
/*  box-shadow: 0vh 0.2vh 0.3vh #d51c57;*/
/*}*/






/*.newsDate img{*/
/*  width: 2vw;*/
/*  height: 3vh;*/
/*  margin-top: 1vh;*/
/*  margin-left: 0.5vw;*/

/*}*/


.department-notices-title {
  grid-row: 1/2;
  grid-column: 1/10;

  padding-left: 1vw;
  font-size: 3vh;
  text-decoration: underline;
  font-family: "Kanit", sans-serif;
}

.department-notices-data-list {
  color: white;
  padding-left: 4vh;
  padding-top: 1vh;
  max-width: 98%;
  vert-align: middle;


}

.department-notices-data {
  grid-column: 1/14;
  grid-row: 2/10;
  font-family: "kanit", sans-serif;

}

.regular {
  font-size: 1.9vh;
}

.smaller {
  font-size: 1.8vh;
}

.department-notices-line-container {
  grid-column: 1/14;
  grid-row: 8/11;
  display: flex;
  justify-content: center;
  align-items: center;
}

.department-notices-line {
  width: 90%;
  height: 0.1vh;
  background: rgb(10, 10, 10);
  box-shadow: 0.1vh 0vh 0.5vh #e9ebeb, -0.1vh 0vh 0.5vh #d3dcdd;
  border-radius: 2vh;
}

</style>