<template>
    <div class="bf" >
        <a href="javascript:" @click="jinru">
            <div class="tp"><img :src="this.$store.state.songName.imgUrl" alt=""></div>
            <div class="wz">
                <p>{{$store.state.songName.songName}}</p>
                <p>{{$store.state.songName.singerName}}</p>
            </div>
        </a>
        <div class="btn">
            <i class="zt"></i>
            <i class="next"></i>
            <i class="xz"></i>
        </div>
    </div>
</template>
<script>
export default {
    
    methods:{
        jinru(){
        // alert(1)
        this.$emit('updatemusicoff', true)
    }
    }
}
</script>
<style scoped>
.bf{
      height: 4.2rem;
      width: 100%;
      position: fixed;
      bottom: 0;
      background: rgba(0,0,0,.9);
      color: #fff;
      font-size: 0;
  }
  .bf a{
      display: block;
      width: 65%;
      height: 100%;
      
  }
  .tp{
    width: 3.75rem;
    height: 3.75rem;
    margin: .2143rem .535rem .2143rem .2143rem;
    float: left;
  }
  .tp img{
      width: 100%;
  }
  .wz{
      width: 65%;
    display: inline-block;
    vertical-align: middle;
  }
  .wz p{
    width: 100%;
    line-height: 2rem;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    font-size: .8571rem;
    color: #fff;
  }
  .btn{
    position: absolute;
    top: 1.0714rem;
    right: .7143rem;
    width: 35%;
    height: 100%;
  }
  .btn i{
    width: 1.786rem;
    height: 1.786rem;
    margin-left: .9rem;
    display: inline-block;
    vertical-align: middle;
    cursor: pointer;
  }
  .zt{
      background: url(http://m.kugou.com/v3/static/images/index/play_icon.png) no-repeat;
      background-size: 100%;
  }
    .next{
      background: url(http://m.kugou.com/v3/static/images/index/next_icon.png) no-repeat;
      background-size: 100%;
  }
    .xz{
      background: url(http://m.kugou.com/v3/static/images/index/download_icon.png) no-repeat;
      background-size: 100%;
  }
      .song-cell .dw{
      width: 1.3rem;
      position: absolute;
      right: 1rem;
  }
  .dw img{
      width: 100%;
  }

  .yd-badge-danger{
    position: absolute;
    left: .5rem;
 }
</style>


