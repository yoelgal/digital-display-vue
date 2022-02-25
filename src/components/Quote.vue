<template>
  <div>
<!--    <div class="dad-joke-title">-->
<!--      <h1>Daily Quote 📖</h1>-->
<!--    </div>-->
<!--    <div class="dad-joke-container">-->
<!--      <p>{{polledData.text}} - {{polledData.author}}</p>-->
<!--    </div>-->
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "Dad-joke",
  data() {
    return {
      polling: null,
      polledData: {
        "text": "Loading",
        "author": "Author"
      }
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const quote = (await (await fetch('https://fathomless-crag-41517.herokuapp.com/quotes')).json()).cs;
        this.polledData = quote
      }, 86400000)
    },
    pullData() {
      axios
          .get('https://fathomless-crag-41517.herokuapp.com/quotes')
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



.dad-joke-title{
  height: 7vh;
  width: 17vw;
  position: relative;
  top: 0.5vh;
  left: 0.5vw;
}

.dad-joke-title h1{
  padding-left: 0.5vw;
}

.dad-joke-container{
  position: relative;
  left: 0.5vw;
  max-width: 21vw;
  height: 8vh;
}

.dad-joke-container p{
  padding-left: 0.5vw;
  font-weight: 400;
  font-size: 1.5vh;
}



</style>