<template>
  <div class="container scroll overflow-hidden">
    <h1><strong>FOOD</strong> Burger</h1>
  </div>
</template>

<script>
export default {
    name: 'Banner'
}
</script>

<style scoped>
  
  .container {
    background-color: #FFF;
    background-image: url(../assets/burger.jpg);
    background-repeat: no-repeat;
    background-position: 0 -250px;
    height: 100vh;
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: flex-start;
  }

  .container h1 {
    color: rgb(230, 193, 48);
    text-align: center;
    font-size: 60px;
    background-color: #25282ebe;
    padding: 20px 40px;
    border-radius: 0 30px 30px 0;

  }


</style>