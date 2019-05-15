<template>
    <div class="play">
        <div class="top">
        <p>{{$store.state.songName.songName}}</p>
          <img src="http://m.kugou.com/v3/static/images/index/goback.png" alt="" @click="fh()">
    </div>
        <div class="playimg">
            <img :src="this.$store.state.songName.imgUrl" alt="">
        </div>
        <div class="lyrics">
            <p>123123</p>
            <p>12123</p>
        </div>
        <div class="jindu"></div>
        <div class="BtnBox">
            <div class="playoperate">
            <i class="prev" @click="pudateMusicThis(-1)"></i>
            <i class="playplay"></i>
            <i class="next" @click="pudateMusicThis(1)"></i>
        </div>
        </div>
        <audio 
            :src="$store.state.songName.url"
            autoplay
            >
        </audio>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'musicc',
        data(){
            return{
            }
        },
    methods:{
        pudateMusicThis (data) {
            this.$store.commit('pudateMusicThis', data)
        },
        fh(){
            this.$emit('updatemusicoff', false)
        },
        musicShow (data) {
            let id = data
            axios(`/proxy/api/v1/song/get_song_info?cmd=playInfo&hash=${id}&from=mkugou&apiver=2&mid=96d25d639d8c552143b5fd2b60b7bed3&userid=0`).then(({data})=>{
            console.log(data)
            this.$store.state.songName = data
            console.log(data.singerName)
            this.$store.state.songName.imgUrl = 'http://singerimg.kugou.com/uploadpic/softhead/400' + data.imgUrl.split('{size}')[1]
            console.log(this.$store.state.songName.imgUrl)
          })
        }
    },
    computed: {
        musicThis () {
            return this.$store.state.musicThis
        },
        musicList () {
            return this.$store.state.songList
        }
    },
    watch: {
        musicThis (to) {
            console.log(to, this.musicList[to])
            let id
            if (this.musicList[to].hash) {
                id = this.musicList[to].hash
            }
            this.musicShow(id)
        }
    }
}
</script>
<style scoped>

.play{
    width: 100%;
    height: 100%;
    background: red;
}
.top{
    z-index: 99;
    height: 3rem;
    width: 100%;
    background: -webkit-linear-gradient(top,rgba(0,0,0,.6),rgba(0,0,0,0));
    top: 1.3rem;
    position: fixed;
    margin-top: 2rem;
    text-align: center;
    line-height: 3rem;
}
.top p{
    color: #ffffff;
    font-size: 16px;
}
.top img{
    position: absolute;
    left: 0;
    top: 0;
    width: .85714rem;
    height: 1.42857rem;
    margin-top: .687265rem;
    display: inline-block;
    margin-left: .5rem; 
}
.playimg{
    width: 10.7143rem;
   
   margin: 1.4286rem auto 0;
}
.playimg img{
    width: 100%;
    margin-top: 70%;
}
.lyrics{
    height: 3.8rem;
    background: purple;
    margin-top: 1rem;
    overflow: hidden;
    text-align: center;
    color: #afabac;
}
.jindu{
    height: 1rem;
    background: pink
}
.BtnBox{
    background: peru;
}
.playoperate{
    height: 5rem;
    width: max-content;
    margin: 0 auto ;
    line-height: 5rem 
}
.prev{    
    width: 2.3214rem;
    height: 2.4rem;
    margin: 0 .8929rem;
    display: inline-block;
    vertical-align: middle;
    background: url(http://m.kugou.com/v3/static/images/index/play_prev.png)no-repeat;
    background-size: 100%;
}
.playplay{    
    width: 3.2143rem;
    height: 3.2143rem;
    margin: 0 .8929rem;
    display: inline-block;
    vertical-align: middle;
    background: url(http://m.kugou.com/v3/static/images/index/play_play.png)no-repeat;
    background-size: 100%;
}
.next{    
    width: 2.3214rem;
    height: 2.4rem;
    margin: 0 .8929rem;
    display: inline-block;
    vertical-align: middle;
    background: url(http://m.kugou.com/v3/static/images/index/play_next.png)no-repeat;
    background-size: 100%;
}
</style>

