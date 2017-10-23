<template>
<div id="app">
  <background-video/>
  <transition name="component-fade" mode="out-in">
    <component @loginSuccess="loginSuccess" @loaded="loaded" :is="currentView" :uname="uname"/>
  </transition>
</div>
</template>

<script>
import backgroundVideo from './components/backgroundVideo.vue'
import loginPage from './components/loginPage.vue'
import loadingPage from './components/loadingPage.vue'
import chatroom from './components/chatroom.vue'

export default {
  name: 'app',
  data () {
    return {
      currentView: 'unlogin',
      uname: ''
    }
  },
  components: {
    backgroundVideo,
    unlogin: loginPage,
    loading: loadingPage,
    logined: chatroom
  },
  methods: {
    loginSuccess: function (username) {
      this.uname = username
      this.currentView = 'loading'
    },
    loaded: function () {
      this.currentView = 'logined'
    },
    changeView: function (targetState) {
      this.currentView = targetState
    }
  }
}
</script>

<style>
body {
  margin: 0px;
  overflow: hidden;
  display: -webkit-flex;
}

#app {
  color: #2c3e50;
  height: 100vh;
  width: 100vw;
  display: flex;
}

.component-fade-enter-active, .component-fade-leave-active {
  transition: opacity .3s ease;
}
.component-fade-enter, .component-fade-leave-to {
  opacity: 0;
}
</style>
