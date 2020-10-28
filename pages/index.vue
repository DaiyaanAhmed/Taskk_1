<template>

  <div class="container">
    <h1>Hello , This is a Basic App</h1>
    <br>
     <button class="btt" @click="$router.push('/m2')" >  Click for Map  </button>
  </div>
 
</template>


<script>
export default {
}
</script>

<style scoped>
.container{
  justify-content: center;
  width:800px;
  margin: 200px auto;
  box-sizing: border-box;
  text-align: center;
}
h1{
  font-size:48px;
  color: rgb(43, 43, 43)
}
.btt{
  width:200px;
  background-color: rgb(167, 167, 167);
  color: black;
  padding:5px;
  border-radius:8px;
}
.btt:hover{
  background-color: rgb(59, 59, 59);
  color: white;
}
</style>>


