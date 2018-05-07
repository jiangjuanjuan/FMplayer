<template>
  <div>
    <h1>{{title}}</h1>
    <audio id="audiold"
            controls src="http://www.egtch.com/t_works/Vuedata/I Am You.mp3">
    </audio>
    <div>
      <input type="button" value="播放" @click="playFn" />
      <input type="button" value="暂停" @click="isPause" />
      <div>
          <li v-for="item in musicList">
            <label><img:src=item.img /></label>
            <span>{{item.name}}</span>
          </li>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'player',
  data () {
    return {
      title:"FM播放器",
      msg: 'Welcome to Your Vue.js App',
      musicList:" "
    }
  },
  created(){
    this.getData();
  },
  methods:{
    getData(){
      axios.get('http://localhost:3698/mp3-list')
           .then((_data) => {
            this.musicList = _data.data.music;
            console.log(this.musicList)
           });
    },
    // 播放方法
    playFn(){
      let _audiold = document.getElementById("audiold");
      _audiold.play();
    },
    //暂停
    isPause(){
      document.getElementById("audiold").pause();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
C:\Users\JJJ\Desktop\item\0227