<template>
  <div class="bus">
    <div class='bus-grid-container'>
      <div class='bus-grid'>
        <div class='bus-title'>
          <div>B</div>
          <div>U</div>
          <div>S</div>
          <div><br /></div>
          <div>T</div>
          <div>I</div>
          <div>M</div>
          <div>E</div>
          <div>S</div>
        </div>
        <div class='square1'>
          <div class="stop1">
            <div class='stop1-name'>The Three Hammers</div>
            <h6>To Edgware</h6>
            <hr />
            <div style='display: flex; flex-direction: row;width: 10vw;justify-content: space-between;margin-top: 1vh;'>
              <h4>{{ polledData.edgware[0] }}</h4>
              <h5>{{ polledData.edgware[1] }}</h5>
            </div>
          </div>
        </div>
        <div class='square2'>
          <div class="stop2">
            <div class='stop2-name'>Mill Hill The Village</div>
            <h6>To Golders Green</h6>
            <hr />
            <div  style='display: flex; flex-direction: row;width: 10vw;justify-content: space-between;margin-top: 1vh;'>
              <h4>{{ polledData.golders[0] }}</h4>
              <h5>{{ polledData.golders[1] }}</h5>
            </div>
          </div>
        </div>
        <div class='square3'>
          <img src="../assets/ThreeHammers.png" alt="">
        </div>
        <div class='square4'>
          <img src="../assets/ToGolders.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      polling: null,
      polledData: {
        edgware: ['loading..', 'loading..'],
        golders: ['loading..', 'loading..'],
      },
      polledDate: "loading timestamp..."
    }
  },
  methods: {
    pollData() {
      this.polling = setInterval(async () => {
        const bus = (await (await fetch('http://localhost:3000/bus')).json());
        // this.polledData = bus
        this.polledData = {
          edgware: [
              bus.edgware[0] || "N/A",
              bus.edgware[1] || "N/A"
          ],
          golders: [
            bus.golders[0] || "N/A",
            bus.golders[1] || "N/A"
          ]
        }

        const date = new Date()
        this.polledDate = date
      }, 40000)
    }
  },
  beforeDestroy() {
    clearInterval(this.polling)
  },
  created() {
    this.pollData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.bus {
  grid-column: 1/5;
  grid-row: 6/10;
}

.bus-grid-container {
  width: 100%;
}

.bus-grid {
  display: grid;
  grid-template-columns: repeat(21, 1fr);
  grid-template-rows: repeat(20, 1fr);
  height: 100%;
  width: 100%;
}

.bus-title {
  grid-column: 1/5;
  grid-row: 1/21;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-right: 2vw;
  font-size: 2.7vh;
  font-weight: bolder;
  font-family: "Kanit", sans-serif;
}

.timer {
  grid-row: 8/11;
  grid-column: 13/15;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  font-size: 5vh;
  padding: 2.5vh;
  border: 0.3vh dashed #cdd9da;
  font-family: "Dongle", sans-serif;
}

.stop1-name,
.stop2-name {
  font-weight: 600;
  position: relative;
  right: 2vw;
  letter-spacing: 0.3vh;
  font-size: 3vh;
  padding-top: 1vh;
  width: 20vw;
  font-family: "Kanit", sans-serif;
  text-decoration: underline;
  text-decoration-thickness: 0.2vh;
  text-decoration-color: #dce3e4;
}

.stop1 h6,
.stop2 h6 {
  margin: 1vh 0 1vh 0;
  letter-spacing: 0.7vh;
  font-size: 2.2vh;
  text-align: center;
  font-family: "Dongle", sans-serif;
  box-shadow: 0.3vh 0.3vh 0.5vh #161414, -0.2vh -0.2vh 0.1vh #5a5252;
  border-radius: 50%;
}

.stop1 h5,
.stop2 h5 {
  padding-top: 0.5vh;
  padding-right: 0vw;
  width: 4vw;
  padding-left: 0.5vw;
  opacity: 0.5;
  font-size: 3vh;
  font-family: "Dongle", sans-serif;
  box-shadow: inset 0.3vh 0.3vh 0.5vh #161414, inset -0.2vh -0.2vh 0.1vh #5a5252;
  border-radius: 2vh;
}

.stop1 h4,
.stop2 h4 {
  font-size: 4vh;
  padding-left: 0.5vw;
  border-radius: 2vh;
  font-family: "Dongle", sans-serif;
  box-shadow: inset 0.1vh 0.1vh 0.5vh #161414, inset -0.1vh -0.1vh 0.1vh #5a5252;
  width: 5vw;
}


.square1 {
  grid-row: 1/10;
  grid-column: 5/13;
}

.square2 {
  grid-row: 11/21;
  grid-column: 5/13;
}

.square3 {
  grid-row: 1/10;
  grid-column: 14/22;
}

.square3 img,
.square4 img {
  margin-top: 2vh;
  margin-left: 2.5vw;
  width: 9.5vw;
  height: 14vh;
  border-radius: 2vh;
  box-shadow: 0.1vh 0.1vh 0.1vh #e70404, -0vh -0vh 1vh rgb(114, 118, 122);
}

.square4 {
  grid-row: 11/21;
  grid-column: 14/22;
}
</style>
