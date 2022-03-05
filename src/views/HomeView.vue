<template>
  <section id="welcome-wrpper">
    <h1 class="hidden">sign In</h1>
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
    }
  }

}
</script>

<style lang="scss">
  .hidden { display: hidden; }
.disabled { opacity: 0.4; }

#welcome-wrapper {
    text-align: center;

    h2 { 
        font-size: 1.5em;
        margin: 30px 0 10px 0;
    }

    input { 
        margin-top: 1em; 
        font-size: 1em; 
        width: 40vw; 
        text-align: center; 
        padding: 1em; 
        border: thin solid; 
        border-radius: round;
        border-color: blue;
    }

    button { 
        font-size: 1em; 
        background-color: blue; 
        color: pink;
        padding: 0.8em 1.2em;
        border: thin solid;
        border-color: blue;
        border-radius: round;
        margin: 1em  0.5em;
    }
}

</style>

