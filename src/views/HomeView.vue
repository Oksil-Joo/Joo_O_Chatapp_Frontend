<template>
<main class="welcomCon">
  <section id="welcome-wrpper">
    <h2>Welcome to the Chat App!</h2>
    <input type="text" name="username" v-model="username" placeholder="Your Name">
    <div class="controls">
      <button
      :class="{ 'disabled': canJoin }"
      :disabled='canJoin'
      @click="goToChat"
     >Join Chat</button>
     <button @click="goToChat">Join Anonymously</button>
   </div>
 </section>
 </main>
</template>

<script>
export default {
  name: "TheLoginPage",

  data() {
    return {
      loggedIn: false,
      username: ''
    }
  },

  computed: {
    canJoin: function() {
      return (this.username.trim() === '')
    }
  },

  methods: {
    goToChat() {
      this.$router.push({ name: 'Chat', params: { ChatUserName: this.username || "Anonymous" }});
    },

  }

}
</script>

<style lang="scss">
.hidden { display: hidden; }
body {
    background-color: #9BB731;
    margin: 0 auto;
    padding: 20px;
    font-family: Helvetica, sans-serif;
    font-size: 16px;
}

.loginCon {
    background-color: white;
    margin:0 auto;
    padding: 58px 66px 58px 66px;
    border-radius: 30px;
    border: thin 1px white;
    box-shadow: 0 1px 30px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,30,0.1);
    margin-top: 30px;
    font-family: Helvetica, sans-serif;
    font-size: 16px;
}
.disabled { opacity: 0.8; }

#welcome-wrapper {
    text-align: center;
}
h2 { 
        font-size: 1.5em;
        margin: 0px 0 10px 0;
    }

    input { 
        margin-top: 1em; 
        font-size: 1em; 
        width: 260px; 
        text-align: center; 
        padding: 1em; 
        border: 3px solid #9BB731;
        border-radius: 10px;
        border-color: #999;
    }

 .controls button { 
        font-size: 1em; 
        background-color: rgb(243, 255, 10); 
        border: 3px solid #9BB731;
        border-radius: 10px;
        margin: 0.3em  0.5em;
        padding: 0.5em 1.2em;
    }
    footer {
  text-align: center;
  color: white;
}

.welcomCon {
  background-color: white;
  width: 400px;
  margin: 20px auto;
  border-radius: 30px;
  border: thin 1px white;
    box-shadow: 0 1px 30px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,30,0.1);
    margin-top: 30px;
    font-family: Helvetica, sans-serif;
    font-size: 16px;
    padding: 30px 10px;
}
</style>

