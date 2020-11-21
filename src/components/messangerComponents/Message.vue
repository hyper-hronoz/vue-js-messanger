<template>
  <div class="messenger__message message" v-bind:class="isUserMessage ? 'user-message' : ''">
    <div class="message__username">
      {{ username }}
    </div>
    <div class="message__text">
      {{ message }}
    </div>
    <div class="message__time">
        {{ time }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Message",
  data: function () {
    return {

    }
  },
  props: {
    isUserMessage: Boolean,
    message: String,
    time: String,
    username: String
  }
}
</script>

<style scoped>
  .message {
    position: relative;
    border: #25a3ff 2px solid;
    border-radius: 32px;
    padding: 13px 32px 26px 32px;
    margin-bottom: 20px;
    align-self: flex-start;
    max-width: 75%;
    color: #000;
  }

  .message__username {
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 7px;
  }

  .message__text {
    font-size: 16px;
  }
  
  .user-message {
    background: #25a3ff;
    border: none;
    align-self: flex-end;
    color: #fff;
  }

  .message__time {
    position: absolute;
    font-size: 12px;
    bottom: 6px;
    right: 24px;
  }
</style>