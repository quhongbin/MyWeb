<script>
import APlayer from 'aplayer';
import "aplayer/dist/APlayer.min.css"; // 引入音乐插件的样式
import EventBus from './eventBus.vue';
export default {
    data(){
        return{
            isVisibleClass: false,
            icons:[{
                    name:'Github',
                    icon:'fa-brands fa-github',
                },
                {
                    name:'Bilibili',
                    icon:'fa-brands fa-bilibili',
                },
                {
                    name:'Email',
                    icon:'fa-solid fa-envelope',
                }
            ],
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
        uploadMarkdown(){
        },
        initAplayer(){
            new APlayer({
                container: document.getElementById('aplayer'),
                fixed: true,
                cover: 'https://p1.music.126.net/5zs7IvmLv7KahY3BFzUmrg==/109951163635241613.jpg?param=300y300',
                audio: this.audio,
                
            });
        },
        // 发出switch-class事件,给bodyApp.vue接收
        toggleClass(){
            this.isVisibleClass = !this.isVisibleClass;
            EventBus.emit("switch-class");
            // console.log(this.isVisibleClass);
        },
    },

    mounted(){
        this.initAplayer();
    },
    components:{
    },
};                      
</script>
<template>
    <div class="nav_container">
        <div class="nav_logo" >
            <img src="../assets/images/qq头像.jpg" alt="logo" width="50px" height="50px"/>
        </div>
        <div class="nav_font" v-for="icon in icons" :key="icon.name">
            <div>
                <i :class="icon.icon"></i>
                {{ icon.name }}
            </div>
        </div>
        <div class="nav_menu">
            <div id="aplayer">

            </div>
            <div class="navSelections">
                <i @click="toggleClass" :class="[isVisibleClass ? 'fa-solid fa-bars-staggered' : 'fa-solid fa-bars']"></i>
            </div>
        </div>
    </div>
</template>

<style scoped>
@import url(../assets/fontawesome/fontawesome-free-6.7.2-web/css/all.css);
@import url(../assets/css/animate.css);
/* @import url(../../node_modules/font-awesome-animation/css/font-awesome-animation.css); */
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
.nav_logo{
    display: inline;
    transition-duration: 1s;
}
.nav_logo:hover{
    transform: scale(1.3);
    transition: transform 0.5s;
}
.nav_font{
    display: flex;
    flex-direction: row;
    justify-content: space-between; 
    align-items: center;
    /* width: 200px; */
}
.nav_menu{
    display: inline;
    width: 100px;
}
.nav_font div{
    margin: 0px 5px 0px 5px;
    font-size: 16px;   
    transition-property: font-size transform;
    transition-duration: 1s;
}
.nav_font div:hover{
    margin: 0px 10px 0px 10px;
    font-size: 36px;
    transform:translate(0px,-10px);
    transition:transform 0.5s;
    text-decoration-line: underline;
    cursor: pointer;
}
i{
    font-size: 20px;
    margin:0px 5px 0px 5px;
}
.fa-solid.fa-bars{
    display: none;
}
/* 切换css样式 */
.navSelections{
    display: none;
} 

@media screen and (max-width: 481px){
    .nav_font{
        display: none;
    }
    .navSelections{
        display: inline;
    } 
    .fa-solid.fa-bars{
        font-size: 50px;
        display: inline;
    }
    .fa-solid.fa-bars-staggered{
        display: inline;
        font-size: 50px;
    }
}
</style>