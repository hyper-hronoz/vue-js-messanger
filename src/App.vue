<template>
  <div id="app">
<!--    <LeftSideBar></LeftSideBar>-->
    <Messenger></Messenger>
  </div>
</template>

<script>
// import LeftSideBar from "./components/LeftSideBar"
import Messenger from "@/components/Messenger"

export default {
  name: 'App',
  components: {
    // LeftSideBar,
    Messenger
  },
  created () {
    document.title = "Sweater";
  },
}
</script>

<style>
  * {
    font-family: "Roboto", sans-serif;
    padding: 0;
    margin: 0;
  }

  body {
    background: #25a3ff;
  }

  @media screen and (min-width: 320px){
    #app {
      display: flex;
      justify-content: center;
      margin: 0 auto;
    }
  }

  @media screen and (min-width: 980px){
    #app {
      max-width: 900px;
    }
  }

  button, input {
    border: none;
    outline: none;
  }
</style>
