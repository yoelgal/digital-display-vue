<template>
  <div class="school-notices">
    <div class="school-overlay1">
      <h2>🎓 School<span style="position: relative;left:2.5vw;display: block;">Notices</span></h2>
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
  grid-column: 12/22;
  grid-row: 1/9;
  display:grid;
  grid-template-rows:repeat(10, 1fr);
  grid-template-columns:repeat(10, 1fr);
  color: white;
}

.school-notices li {
  font-size: 1rem;
}

.school-overlay1{
  grid-row: 1/4;
  grid-column:1/5;
  background: #2a2828;
  border-bottom-right-radius: 2vh;
  box-shadow: 0 0 0.1vh 0.5vh #1d94d9, 0 0 0.1vh 1vh #4c2bed;
}

/*.school-ellipse1{*/
/*  background: linear-gradient(#e8e50e, #e95b1e);*/
/*  border-radius: 50%;*/
/*  width: 3vw;*/
/*  height: 5vh;*/
/*  position: relative;*/
/*  left: 15vw;*/
/*  top: 6.5vh;*/
/*}*/

/*.school-ellipse2{*/
/*  background: linear-gradient(#e8e50e, #e95b1e);*/
/*  border-radius: 50%;*/
/*  width: 3vw;*/
/*  height: 5vh;*/
/*  left: 24vw;*/
/*  top: 6vh;*/
/*  position: relative;*/


/*}*/

.school-overlay1 h2{
  padding-top: 0.5vh;
  font-size: 1.4em;

}


.school-overlay2{
  background: #2a2828;
  box-shadow: 0 0 0.1vh 0.5vh #1d94d9, 0 0 0.1vh 1vh #4c2bed;
  border-top-right-radius: 2vh;
  border-bottom-right-radius: 2vh;
  grid-row: 3/9;
  z-index:-1;
  grid-column: 1/6;

  overflow: hidden;
}

.school-overlay2 ul{
  position: relative;
  top: 5vh;
  font-weight: 500;
  line-height: 2.5vh;
  left: 2vw;
  font-size: 1.3vh;
  max-width: 14vw;
}

.school-overlay3{
  background: #2a2828;
  box-shadow: 0 0 0.1vh 0.5vh #1d94d9, 0 0 0.1vh 1vh #4c2bed;
  grid-row: 6/11;
  grid-column: 1/11;
  z-index:-2;
  border-top-right-radius: 2vh;

}

.school-overlay3 ul{
  position: relative;
  left: 19.5vw;
  top: 1vh;
  max-width:14vw;
  max-height:10vh;
  font-size: 1.3vh;
  font-weight: 500;
  line-height: 2.5vh;
}

.school-overlay4{
  background: #2a2828;
  box-shadow: 0 0 0.1vh 0.5vh #1d94d9, 0 0 0.1vh 1vh #4c2bed;

  grid-row: 1/7;
  position: relative;

  left: 1vw;
  z-index: -3;
  border-top-left-radius: 2vh;
  grid-column: 3/11;
  border-top-right-radius: 2vh;
  overflow: hidden;

}

.school-overlay4 ul{
  position: relative;
  left: 11.5vw;
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