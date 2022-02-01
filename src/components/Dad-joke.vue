<template>
  <div class="dad-joke">
    <p>
      {{
        polledData
      }}
    </p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "Dad-joke",
  data() {
    return {
      polling: null,
      polledData: "loading joke..."
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const joke = (await (await fetch('https://digital-display-express.herokuapp.com/dad-joke')).json()).newText;
        this.polledData = joke
      }, 86400000)
    },
    pullData() {
      axios
          .get('https://digital-display-express.herokuapp.com/dad-joke')
          .then(response => (this.polledData = response.data.newText))
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
.dad-joke {
  grid-column: 1/13;
  grid-row: 2/9;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 2vh;
  font-style: italic;
  padding: 5%;
}
</style>