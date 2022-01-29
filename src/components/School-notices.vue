<template>
  <div class="school-notices">
    <div class='school-notices-grid'>
      <div class='school-notices-title'>School Notices</div>
      <div class='school-notices-data'>
        <div class=notice1>
          <ul>
            <li>Lorem ipsum dolor sit, amet consectetur adipisicing elit.</li>
          </ul>
        </div>
        <div class=notice2>
          <ul>
            <li>Lorem ipsum dolor sit, amet consectetur adipisicing elit.</li>
          </ul>
        </div>
        <div class=notice3>
          <ul>
            <li>Lorem ipsum dolor sit, amet consectetur adipisicing elit.</li>
          </ul>
        </div>

      </div>
      <div class=school-notices-underline></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "School-notices"
}
</script>

<style scoped>
.school-notices {
  grid-column: 5/8;
  grid-row: 1/3;
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