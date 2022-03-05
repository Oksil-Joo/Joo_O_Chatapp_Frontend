<template>
  <main>
    <h1 class="welcome-message">welcome {{ ChatUserName }}!</h1>

    <section id="chat">
      <!-- left hand side -> users go here -->
      <section id="chat-users-ui">
        <h2>Current Users:</h2>

        <!-- lay this out however you like - we're just using a list -->
        <ul id="current-users">
          <!-- render a users component for every connected user here -->
        </ul>
      </section>

      <!-- right hand side -> Chat UI -->
      <section id="chat-messages-ui">
        <ChatMessage
          v-for="msg in messages"
          :key="msg.id"
          :message="msg.message"
          :user="msg.user"
        />
        <!-- render a omponent for every message -->
        <section id="text-wrapper">
          <textarea @keyup.enter="sendOnEnter" id="message" v-model="message" placeholder="What's on your mind?" ></textarea>

          <button id="sendMessage"
          @click="sendMessage"
          :disabled="messageContent"
          :class="{'disabled' : messageContent}"
          >
            <i class="fa fa-envelope" style="font-size:48px;color:black"></i>
          </button>
        </section>
      </section>
    </section>

  </main>
</template>

<script>
import io from "socket.io-client";
import vars from "@/env.js";
import ChatMessage from "@/components/ChatMessage.vue";

export default {
  name: "TheChatComponent",

  props: {
    ChatUserName: String
  },

  mounted() {
    let vm = this;

    this.socket.on("CONNECTED", (id) => {
      // debugger;
      vm.socketID = id;
    })

  this.socket.on('MESSAGE', (message) => {
      // debugger;
      vm.messages = [...vm.messages, message];
      console.log(message);
    })

    this.socket.on('TEST_FOR_EVENT', (data) => {
      console.table(data);
    })
  },

  computed: {
    messageContent: function() {
      return this.message.trim() === '';
    }

  },

  data() {
    return {
      //store the connection ID so we can use it later
      socketID: '',
      message: '',
      messages: [],

      socket: io(vars.basePath, {
        withCredentials: false,
        extraHeaders: {
          'Access-Control-Allow-Origin': '*'
        }
      })
    }
  },

  methods: {
    sendMessage() {
      this.socket.emit('SEND_MESSAGE', { user: this.ChatUserName || "Anonymous", message: this.message })

      this.message = '';
    },

    sendOnEnter() {
      if (this.messageContent == false && event.keyCode == 13) {
        this.sendMessage();
      } else {
        this.socket.emit("TYPING", { user: this.username || "Anonymous" });
      }
    }
  },

  components: {
    ChatMessage
  }
}
</script>

<style lang="scss">
.disabled { opacity: 0.4; }

#chat { 
    display: grid;
    grid-template-columns: 1fr 3fr;
}

.welcome-message {
    font-size: 1.3em;
    margin: 0.8em 0;
    padding-left: 0.8em;
}

#chat-users-ui {
    border-right: thin solid #333;
}

#chat-users-ui, #chat-messages-ui {
    padding: 0.8em;
    position: relative;
}

#chat-users-ui {
    h2 { font-size: 1.3em; }
}

#current-users { margin-top: 1em; }

#text-wrapper { position: relative; }

textarea { 
    width: 70%; 
    min-height: 100px;
    border: thin solid border-color blue ;
    border-radius: round;
    margin-top: 1em;
    padding: 1em;
    font-size: 1em;
    resize: none;
}

#sendMessage {
    position: relative;
    top: -60px;
    left: 10px;
    border: none;
    width: 50px;
    height: 50px;
    font-size: 1.5em;
    text-align: center;
    border-radius: round;

    i { color: blue; }
}
</style>