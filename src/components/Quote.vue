<template>
  <div class="facts">
    <div class="facts-title-bar">
      <ion-icon class="book-icon" name="book"></ion-icon>
      <div  class='fact-title'>Daily Quote</div>
      <ion-icon class="book-icon" name="book"></ion-icon>

    </div>
    <div class="daily-fact-container">
      <div class="daily-fact" :class="polledData.text.length>200?'smaller': 'regular'">
        <p>
          {{polledData.text}} - {{polledData.author}}
        </p>

      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Facts",
  data() {
    return {
      polling: null,
      polledData: {
        text: 'Loading quote...',
        author: 'Loading author...'
      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const fact = (await (await fetch('https://digital-display-express.herokuapp.com/quotes')).json()).cs;
        this.polledData = fact
      }, 86400000)
    },
    pullData() {
      axios
          .get('https://digital-display-express.herokuapp.com/quotes')
          .then(response => (this.polledData = response.data.cs))
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
.facts {
  grid-column: 5/9;
  grid-row: 8/10;
  display: flex;
  flex-direction: column;
}

.facts-title-bar {
  display: flex;
  justify-content: center;
  align-items: center;
}

.fact-title {
  letter-spacing: 1vh;
  padding-left: 1vw;
  font-size: 4vh;
  text-decoration: underline;
  font-family: "Kanit", sans-serif;
}

.book-icon {
  padding-top: 1vh;
  padding-left: 0.5vw;
  height: 5vh;
  width: 3vw;
}

.daily-fact-container {
  width: 100%;
  height: 100%;
  text-align: center;
}

.daily-fact p {
  display: block;
  font-family: "Kanit", sans-serif;
  align-self: center;
  vertical-align: middle;
  padding-top: 2%;
  padding-left: 6%;
  padding-right: 6%;
  justify-content: center;
  /* font-family: "Dongle", sans-serif; */
}

.regular {
  font-size: 2vh;
}

.smaller {
  font-size: 1.5vh;
}

</style>