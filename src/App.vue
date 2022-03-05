<template>
  <div id="app">
    <header>
      <h1 class="hidden">Welcome to the Chat App</h1>
      <h2>Chat app with Vue CLI, Express and socket.io</h2>
    </header>
    <h3>Dynamic Content Below:</h3>
      <router-view> </router-view>
    <h3>Dynamic Content Above</h3>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  text-align: center;
  background-color: blue;
  padding: 1em 0.8em;
  color: white;
}
header {
  .hidden { display: none; }
  h2 { font-size: 2em; margin-bottom: 0.8em; }
}
</style>