<template>
  <div class="messenger__profile profile">
    <img class="profile__img" :src="avatar" />
    <div class="profile__nickname">
      {{ login }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Profile",
  props: {
    login: String
  },
  data: function () {
    return {
      avatar: "profile.png",
    }
  }
}
</script>

<style scoped>
  .profile {
    display: flex;
    align-items: center;
  }

  .messenger__profile {
    margin-top: 42px;
    margin-bottom: 32px;
  }

  .profile__img {
    width: 54px;
    height: 54px;
    border-radius: 50%;
  }

  .profile__nickname {
    margin-left: 36px;
    font-size: 18px;
    font-weight: 800;
  }
</style>