<script>
import APlayer from 'aplayer'
import 'aplayer/dist/APlayer.min.css'
export default {
  data() {
    return {
      name: 'Footer',
      audio: [
        {
          name: '第三人称',
          artist: 'WF_Li第三人称ang',
          url: 'http://music.163.com/song/media/outer/url?id=1957883626.mp3',
          cover:
            'http://p2.music.126.net/7o8ZVb5OlN32S6WdEztiJw==/109951167390493466.jpg?param=130y130',
        },
        {
          name: '迷途羔羊',
          artist: '曾小朴',
          url: 'http://music.163.com/song/media/outer/url?id=1485090394.mp3',
          cover:
            'http://p2.music.126.net/NpOyonteBHlH97tCZHlXpA==/109951165371157421.jpg?param=130y130',
        },
        {
          name: '理想三旬',
          artist: '陈鸿宇',
          url: 'http://music.163.com/song/media/outer/url?id=31445772.mp3',
          cover:
            'http://p2.music.126.net/NpOyonteBHlH97tCZHlXpA==/109951165371157421.jpg?param=130y130',
        },
      ],
    }
  },
  components: {},
  methods: {
    initAplayer() {
      new APlayer({
        container: document.getElementById('aplayer'),
        fixed: true,
        cover:
          'https://p1.music.126.net/5zs7IvmLv7KahY3BFzUmrg==/109951163635241613.jpg?param=300y300',
        audio: this.audio,
      })
    },
  },
  mounted() {
    this.initAplayer()
  },
}
</script>

<template>
  <div class="footer">
    <!-- 备案号和版权信息 -->
    <p>备案号：蜀ICP备2024111078号-1</p>
    <p>版权所有 &copy; 2023 quhongbin</p>
    <div id="aplayer"></div>
  </div>
</template>

<style scoped>
.footer {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: row;
  padding: 20px;
  background-color: rgba(222, 222, 222, 0.8);
  position: fixed;
  bottom: 0;
  width: 100%;
}

.footer p {
  margin: 0;
  padding: 0;
  font-size: 12px;
  color: #333;
}
@media screen and (max-width: 481px) {
  .footer {
    display: none;
  }
  
}
</style>
