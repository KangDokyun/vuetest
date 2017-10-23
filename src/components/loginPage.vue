<template>
<div id="loginPage">
  <div id="title1">Share your happiness </div>
  <div id="title2">Chat Room</div>
  <div id="title3">
    <span id="icon"><i class="fa fa-user"></i></span>
    <input id="uname" type="text" spellcheck="false" placeholder="Enter your name" 
      v-focus v-model="username" @keydown.enter="checkUname"/>
    <button id="login-btn" type="button" @click="checkUname">Chat Now!</button>
  </div>
  <transition>
    <p id="errorMsg" v-show="showError">{{ errorMsg }}</p>
  </transition>
</div>
</template>

<script>
export default {
  name: 'loginPage',
  data () {
    return {
      errorMsg: 'User name mustn\'t be or contain empty char',
      username: '',
      showError: false
    }
  },
  components: {

  },
  methods: {
    checkUname: function () {
      var reg = /\s+/
      if (this.username.length === 0 || reg.test(this.username)) {
        this.showError = true
        setTimeout(() => {
          this.showError = false
        }, 2000)
      } else {
        this.$emit('loginSuccess', this.username)
      }
    }
  },
  directives: {
    focus: {
      inserted: function (el) {
        el.focus()
      }
    }
  }
}
</script>

<style scoped>
#loginPage {
  display: -webkit-flex;
  flex-flow: column nowrap;
  justify-content: start;
  align-items: center;
  margin: auto;
}

#title1 {
  color: #FFFFFF;
  margin-bottom: 1rem;
  font-size: 1rem;
  font-weight: lighter;
}

#title2 {
  -webkit-transform: scale(0.8,1.2);
  font-size: 7rem;
  color: #FFFFFF;
  font-weight: bolder;
}

#title3 {
  margin-top: 1rem;
  margin-bottom: 8rem;
  display: flex;
  flex-flow: row nowrap;
  justify-content: center;
  align-items: center;
  height: 2.5rem;
  font-size: 1.5rem;
}

#icon {
  -webkit-transform: scale(0.8,0.8);
  border: 1;
  background:transparent;
  color:#FFF
}

#uname {
  border: 0;
  margin-left: 1em;
  padding-left: 1em;
  height: 2.5rem;
  width: 10rem;
  font-size: 1.1rem;
  background: rgba(255,255,255,0.2);
  color: #FFFFFF;
}

#login-btn {
  border: 0;
  height: 2.5rem;
  width: 8rem;
  font-size: 1.1rem;
  background: rgba(41,56,95,1);
  color: #FFFFFF;
}

#errorMsg {
  margin-top: 1rem;
  color:#FF0000;
  font-weight:lighter;
}

.v-enter-active, .v-leave-active {
  transition: opacity .5s
}

.v-enter, .v-leave-to {
  opacity: 0
}
</style>