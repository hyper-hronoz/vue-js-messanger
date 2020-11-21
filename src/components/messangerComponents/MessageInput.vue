<template>
  <form action="/" @submit.prevent="submit" class="messenger__input input-message">
    <input type="text" class="input-message__input" v-model="message">
    <button type="submit" class="input-message__send">
      <img :src="sendImg" alt="">
    </button>
  </form>
</template>

<script>

export default {
  name: "MessageInput",
  data: function () {
    return {
      sendImg: "sendButton.png",
      message: "",
      data: ""
    }
  },
  methods: {
    submit() {
      this.$emit("message_sent",
         this.message
      )
      this.$emit("get_messages")
      this.message = ""
    },
  },
}
</script>

<style scoped>
  @media screen and (min-width: 320px){
    .input-message {
      position: fixed;
    }
    .input-message__input {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      box-sizing: border-box;
      padding: 15px 80px 15px 37px;
      width: 100%;
      font-size: 15px;
      font-weight: 700;
      height: 50px;
      box-shadow: rgba(0, 0, 0, .5) 0 0 10px;
    }
    .input-message__send {
      background: none;
      position: fixed;
      bottom: 5px;
      right: 25px;
    }
  }

  @media screen and (min-width: 980px)  {
    .input-message {
      position: relative;
    }
    .input-message__input {
      position: relative;
    }
    .input-message__send {
      position: absolute;
      cursor: pointer;
      right: 19px;
      top: 9px;
      background: none;
    }
  }


</style>