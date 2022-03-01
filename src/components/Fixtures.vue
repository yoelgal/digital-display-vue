<template>
  <div class="fixtures">
<!--    <div class="fixtures-overlay1"></div>-->

  </div>
</template>

<script>
export default {
  name: "Fixtures"
}
</script>

<style scoped>
.fixtures {
  grid-column: 12/24;
  grid-row:23/31;
  background-color: #2a2828;
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: repeat(10, 1fr);
}
/*which sport,  date, team, opponent*/
.fixtures-overlay1{
  border: 2px solid red;

}




</style>