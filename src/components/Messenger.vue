<template>
    <div class="app__messenger messenger">
      <div class="messages">
        <Message v-for="message in messages" v-bind:key="message.text" v-bind:message="message.message"
                 v-bind:time="message.time" v-bind:isUserMessage="userId == message.userId" v-bind:username="message.username"/>
      </div>
      <MessageInput @message_sent="postMessages"></MessageInput>
      <Login @username="getUsername"></Login>
    </div>
</template>

<script>
import Message from "@/components/messangerComponents/Message";
import MessageInput from "@/components/messangerComponents/MessageInput";
import Login from "@/components/Login";
import axios from "axios";

export default {
  name: "Messenger",
  data: function () {
    return {
      messages: Array,
      userId: String,
      username: String,
    }
  },
  components: {
    Message,
    MessageInput,
    Login
  },
  methods: {
    getMessages() {
      axios.get('http://192.168.0.14:8080/message').then(response => (this.messages = response.data))
      console.log(this.messages)
    },
    postMessages(e) {
      axios.post("http://192.168.0.14:8080/message", {
        message: e,
        userId: this.userId,
        username: this.username,
      }).then(() => (this.getMessages()))
    },
    getUsername(e) {
      this.username = e
    }
  },
  mounted() {
    if (sessionStorage.getItem("userId") != null) {
      this.userId = sessionStorage.getItem("userId")
    } else {
      axios.post("http://192.168.0.14:8080/login").then(response => {
        this.userId = response.data
        sessionStorage.setItem("userId", response.data)
      })
    }
    setInterval(() => { this.getMessages() }, 1000)
  }
}
</script>

<style scoped>

/* хром, сафари */
.messages::-webkit-scrollbar { width: 0; }

/* ie 10+ */
.messages { -ms-overflow-style: none; }

/* фф (свойство больше не работает, других способов тоже нет)*/
.messages { overflow: -moz-scrollbars-none; }

.messenger {
  box-shadow: rgba(0, 0, 0, .5) 0 0 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

@media screen and (min-width: 320px){
  .messenger {
    box-sizing: border-box;
    height: 100vh;
    width: 100%;
    padding: 30px 20px;
    background: #fff;
  }
}

.messages {
  display: flex;
  flex-direction: column;
  overflow: auto;
  margin-bottom: 30px;
}

</style>