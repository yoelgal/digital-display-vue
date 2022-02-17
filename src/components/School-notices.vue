<template>
  <div class="school-notices">
    <div class="school-overlay1">
      <h2>🎓 School Notices</h2>
    </div>
    <div class="school-overlay2">
      <ul>
        <li>2nd XI football team enjoy another big win and continue their unbeaten streak!</li>
      </ul>
      <div class="school-ellipse1"></div>
    </div>
    <div class="school-overlay3">
      <ul>
        <li>New groundbreaking dashboard system being trialled in the CS department - Dubbed as a 'work of art'</li>
      </ul>
    </div>
    <div class="school-overlay4">
      <ul>
        <li>Chicken Katsu Curry: Contender for Meal of the Year?</li>
      </ul>
      <div class="school-ellipse2"></div>
    </div>
<!--    <div class='school-notices-grid'>-->
<!--      <div class='school-notices-title'>School Notices</div>-->
<!--      <div class='school-notices-data'>-->
<!--        <div class=notice1>-->
<!--          <ul>-->
<!--            <li>2nd XI football team enjoy another big win and continue their unbeaten streak!</li>-->
<!--          </ul>-->
<!--        </div>-->
<!--        <div class=notice2>-->
<!--          <ul>-->
<!--            <li>Chicken Katsu Curry: Contender for Meal of the Year?</li>-->
<!--          </ul>-->
<!--        </div>-->
<!--        <div class=notice3>-->
<!--          <ul>-->
<!--            <li>New groundbreaking dashboard system being trialled in the CS department - Dubbed as a 'work of art'</li>-->
<!--          </ul>-->
<!--        </div>-->

<!--      </div>-->
<!--      <div class=school-notices-underline></div>-->
<!--    </div>-->
  </div>
</template>

<script>
export default {
  name: "School-notices"
}
</script>

<style scoped>
.school-notices {
  overflow: hidden;
  grid-column: 5/9;
  grid-row: 1/4;
  display:grid;
  grid-template-rows:repeat(10, 1fr);
  grid-template-columns:repeat(10, 1fr);
}

.school-notices li {
  font-size: 1.5vh;
}

.school-overlay1{
  grid-row: 1/4;
  grid-column:1/5;
  box-shadow: 0.2vh 0.2vh 0.1vh 0.2vh #fff;
  background: linear-gradient( to bottom right, rgba(237, 252, 7), rgba(255, 107, 17));

  border-bottom-right-radius: 2vh;
}

.school-ellipse1{
  background: linear-gradient(#e8e50e, #e95b1e);
  border-radius: 50%;
  width: 3vw;
  height: 5vh;
  position: relative;
  left: 15vw;
  top: 6.5vh;
}

.school-ellipse2{
  background: linear-gradient(#e8e50e, #e95b1e);
  border-radius: 50%;
  width: 3vw;
  height: 5vh;
  left: 24vw;
  top: 4vh;
  position: relative;


}

.school-overlay1 h2{
  text-align: center;
  padding-top: 0.5vh;
  font-size: 1.6em;

}


.school-overlay2{
  background: linear-gradient(to bottom right, #4fd3e5, #1183c2);
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  grid-row: 3/9;
  z-index:-1;
  grid-column: 1/6;
  box-shadow: 0.2vh 0vh 0.1vh 0.3vh #fff;
  overflow: hidden;
}

.school-overlay2 ul{
  color: black;
  position: relative;
  top: 4vh;
  font-weight: 500;
  line-height: 2.5vh;
  left: 2vw;
  font-size: 1.3vh;
  max-width: 14vw;
}

.school-overlay3{
  box-shadow: 0.1vh 0.1vh 0.1vh 0.4vh #fff;
  background: white;
  grid-row: 6/11;
  grid-column: 1/11;
  z-index:-2;
  border-top-right-radius: 2vh;
  background: linear-gradient(to bottom left, #4fd3e5, #1183c2);
}

.school-overlay3 ul{
  position: relative;
  left: 19vw;
  top: 1vh;
  max-width:15vw;
  max-height:10vh;
  font-size: 1.3vh;
  font-weight: 500;
  line-height: 2.5vh;
}

.school-overlay4{
  box-shadow: 0.2vh 0.2vh 0.1vh 0.6vh #111111;
  background: white;
  grid-row: 1/7;
  position: relative;
  background: linear-gradient(to bottom right, #4fd3e5, #1183c2);
  left: 1vw;
  z-index: -3;
  border-top-left-radius: 2vh;
  grid-column: 3/11;
  border-top-right-radius: 2vh;
  overflow: hidden;

}

.school-overlay4 ul{
  position: relative;
  left: 11vw;
  top: 1vh;
  font-size: 1.3vh;
  max-width:12vw;
  font-weight: 500;
  line-height: 2.5vh;
}














.school-notices-grid {
  width: 100%;
  display: grid;
  grid-auto-columns: repeat(13, 1fr);
  grid-template-rows: repeat(10, 1fr);
}

.school-notices-title {
  grid-row: 1/4;
  grid-column: 1/14;
  padding-left: 1vw;
  font-family: "kanit", sans-serif;
  text-decoration: underline;
  font-size: 3vh;
}

.school-notices-data {
  grid-row: 3/8;
  grid-column: 1/14;
  display: flex;
  flex-direction: column;
  align-items: left;
  padding-left: 3vw;
  margin-top: 2vh;
  font-family: "kanit", sans-serif;
}

.notice1,
.notice2,
.notice3 {
  font-size: 1.5vh;
}

</style>