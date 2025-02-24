<script>
import APlayer from 'aplayer';
import "aplayer/dist/APlayer.min.css"; // 引入音乐插件的样式
import popupApp from './popupApp.vue';
export default {
    data(){
        return{
            Markdowncontent: "",
            BarsClass: true,
            audio: [
                {
                    name:'第三人称',
                    artist: 'WF_Li第三人称ang',
                    url: 'http://music.163.com/song/media/outer/url?id=1957883626.mp3',
                    cover: 'http://p2.music.126.net/7o8ZVb5OlN32S6WdEztiJw==/109951167390493466.jpg?param=130y130',
                    lrc: '[00:00.00] (,,•́ . •̀,,) 刚刚开始学钢琴弹的hhhh',
                },
            ],


        };
    },
    

    methods: {
        uploadMarkdown(e){
            const file = e.target.files[0];
            if(file){
                var reader = new FileReader();
                reader.onload = (e) => {
                    this.$emit("MarkdownContentToBody", e.target.result);
                };
                reader.readAsText(file);
            };
        },
        initAplayer(){
            new APlayer({
                container: document.getElementById('aplayer'),
                fixed: true,
                cover: 'https://p1.music.126.net/5zs7IvmLv7KahY3BFzUmrg==/109951163635241613.jpg?param=300y300',
                audio: this.audio,
                
            });
        },
        changeBarsClass(){
            this.BarsClass = !this.BarsClass;
        },
    },

    mounted(){
        this.initAplayer();
    },
    components:{
        popupApp,
    },
};                      
</script>
<template>
    <div class="nav_container">
        <div class="nav_logo">
            <img src="../assets/images/qq头像.jpg" alt="logo" width="50px" height="50px"/>
        </div>
        <div class="nav_font">
            <div><i class="fa-brands fa-github"></i>Github</div>
            <div><i class="fa-brands fa-bilibili"></i>Bilibili</div>
            <div><i class="fa-solid fa-envelope"></i>Email</div>
        </div>
        <div class="nav__menu">
            <div id="aplayer">

            </div>
            <div class="navSelections">
                <i @click="changeBarsClass" :class="{'fa-solid fa-bars':BarsClass,'navSelectionsMenu':!BarsClass}"></i>
                <div class="navSelectionsMenu">
                    <popupApp></popupApp>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped>
@import url(../assets/fontawesome/fontawesome-free-6.7.2-web/css/all.css);
.nav_container{
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 10px 20px;
    background-color: rgba(245, 245, 245, 0.7);
}
.nav_logo>img:nth-child(1){
    border-radius: 20%;
    border: 3px solid gray;
}
.nav_font{
    display: flex;
    justify-content: space-between;
    /* align-items: center; */
    /* width: 200px; */
}
.nav_font div{
    margin: 0px 10px 0px 10px;
}
i{
    font-size: 20px;
    margin:0px 5px 0px 5px;
}
@media screen and (max-width: 481px){
    .nav_font{
        display: none;
    }
    .fa-solid.fa-bars{
        font-size: 50px;
    }
    /* 切换css样式 */
    .navSelectionsMenu{
        display: inline;
        width: 50px;
        height: 50px;
        background-color: royalblue ;
    } 
}
</style>