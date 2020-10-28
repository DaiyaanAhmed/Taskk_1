<template>
    <header>
        <div class="spacer">
        <ul class="nav">
            <li class="navit"> <nuxt-link to="/">Home</nuxt-link> </li>
            <li class="navit"> <nuxt-link to="/m2">Map</nuxt-link> </li>
        </ul>
        </div>
    </header>
</template>

<style scoped>
header{
    background-color: black;
    height:60px;
    width:100%;
    box-sizing: border-box;
    z-index: 100;
    align-items: center;
    display: flex;
    justify-content: space-around;
    padding: 0 20px;
}
.spacer{
    flex:1;
}
.nav{
    list-style-type: none;
    padding:0;
    margin: 0;
    display: flex;
    float: right;
}
.navit {
  margin: 0 10px;
}

.navit{
  text-decoration: none;
  color: white;
}

.navit :hover,
.navit :active {
  color: red;
}
</style>