<template>
  <div class="department-notices">
    <div class='department-notices-grid'>
      <div class='department-notices-title'>News Headlines
      </div>
      <div class='department-notices-data'>
        <ul class="department-notices-data-list"  :class="this.textLength>295?'smaller': 'regular'" >
          <hr/>
          <li>{{ polledData[0] }}</li>
          <hr/>
          <li>{{ polledData[1] }}</li>
          <hr/>
          <li>{{ polledData[2] }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

// const isOverflown = ({ clientHeight, scrollHeight }) =>
//     scrollHeight > clientHeight;
//
// const parent = document.querySelector('.text-container')
// console.log(isOverflown(parent));
//
// const resizeText = ({ element, parent }) => {
//   let i = 3;
//   let overflow = false;
//   const maxSize = 128;
//
//   while (!overflow && i < maxSize) {
//     element.style.fontSize = `${i}px`;
//     overflow = isOverflown(parent);
//     if (!overflow) i++;
//   }
//
//
//   element.style.fontSize = `${i - 1}px`;
// };
//
// resizeText({
//   element: document.querySelector(".text"),
//   parent: document.querySelector(".text-container"),
// });


export default {
  name: "Department-notices",
  data() {
    return {
      polling: null,
      startNum: 0,
      polledData: ['loading...', 'loading...', 'loading...'],
      textLength: 400
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const news = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/news')).json());
        this.startNum < 12 ? this.startNum += 3 : this.startNum = 0
        this.polledData = [news[this.startNum+0].title, news[this.startNum+1].title, news[this.startNum+2].title]
        this.textLength = this.polledData[0].length + this.polledData[1].length + this.polledData[2].length
      }, 60000)
    },
    pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/news')
          .then(response => (this.polledData =  [response.data[this.startNum+0].title, response.data[this.startNum+1].title, response.data[this.startNum+2].title]))
      this.textLength = this.polledData[0].length + this.polledData[1].length + this.polledData[2].length
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
.department-notices {
  grid-column: 9/12;
  grid-row: 1/4;
}

.department-notices-grid {
  display: grid;
  grid-template-rows: repeat(10, 1fr);
  grid-template-columns: repeat(13, 1fr);
  width: 100%;
}

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