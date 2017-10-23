<template>
<div id="chatroom">
  <div id="msg-list-box" class="am-u-lg-centered myscroll am-scrollable-vertical">
    <ul id="msg-list" class="am-comments-list am-comments-list-flip">
      <li v-for="msg in msgs" :key="msg.id"  :class="['am-comment', (msg.author==uname)?'am-comment-primary am-comment-flip':'am-comment-highlight']">
        <img src="http://s.amazeui.org/media/i/demos/bw-2014-06-19.jpg?imageView/1/w/96/h/96" class="am-comment-avatar"/>
        <div class="am-comment-main">
          <hearder class="am-comment-hd">
            <div class="am-comment-meta">
              <a class="am-comment-author">{{msg.author}}</a> at {{msg.time}}
            </div>
          </hearder>
          <div class="am-comment-bd">
            <p>{{msg.text}}</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
  <div id="msg-input-area" class="am-u-lg-centered am-input-group" >
    <span class="input--minoru">
        <input class="am-form-field input__field--minoru" id="send-msg" type="text" v-model="currentMsg" @keydown.enter="sendMsg"/>
    </span>
  </div>
</div>
</template>

<script>
export default {
  name: 'chatroom',
  props: {
    uname: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      msgCnt: 0,
      currentMsg: '',
      msgs: []
    }
  },
  methods: {
    getCurrentTime: function () {
      var time = new Date()
      var str = ''
      str += time.getFullYear() + '-'
      str += time.getUTCMonth() + 1 + '-'
      str += time.getUTCDate() + ' '
      str += time.getHours() + ':'
      str += (time.getMinutes() < 10) ? ('0' + time.getMinutes()) : (time.getMinutes())
      return str
    },
    sendMsg: function () {
      this.msgs.push({
        id: this.msgCnt++,
        author: this.uname,
        time: this.getCurrentTime(),
        text: this.currentMsg
      })

      // For test
      this.msgs.push({
        id: this.msgCnt++,
        author: 'EchoRobot',
        time: this.getCurrentTime(),
        text: this.currentMsg
      })

      this.currentMsg = ''
    }
  }
}
</script>

<style scoped>
#chatroom {
  width: 100%;
  display: flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  align-items: center;
}

#msg-list-box {
  width: 60%;
  height: 27em;
  margin-right: auto;
  margin-left: auto;
  margin-top: 5rem;
  background: rgba(255,255,255,0.2);
}

#msg-input-area {
  margin-top:2em; 
  width:60%;
}

#send-msg {
  border:0;
  background: rgba(255,255,255,0.2); 
  color:#FFF
}

.am-comment-author {
  color: rgba(59, 180, 242, 1);
}

.am-comment-avatar {
  width: 48px;
  height: 48px;
}

.am-comment-bd{
  color:rgba(255,255,255,0.8)
}
</style>