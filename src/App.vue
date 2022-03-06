<template>
  <div id="app">
    <h1 class="hidden">chat app with Node, express, and the Vue cli</h1>
    <header>    
        <img src="../src/assets/talk.svg" width="100" alt="talk">
        <h2> My Chat App</h2>
    </header>

      <router-view> </router-view>

  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #999;
}
.hidden { display: none; }
header {
  text-align: center;
  padding: 0em;
  color: white;
}
header {

  h2 { font-size: 3em; }
}
</style>