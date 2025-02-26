<script>
import APlayer from 'aplayer';
import "aplayer/dist/APlayer.min.css"; // 引入音乐插件的样式
export default {
    data(){
        return{
            Markdowncontent: "",
            BarsClass: true,
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
    },
};                      
</script>
<template>
    <div class="nav_container">
        <div class="nav_logo">
            <img src="../assets/images/qq头像.jpg" alt="logo" width="50px" height="50px"/>
        </div>
        <div class="nav_font" v-for="icon in icons" :key="icon.name">
            <div>
                <i :class="icon.icon"></i>
                {{ icon.name }}
            </div>
        </div>
        <div class="nav__menu">
            <div id="aplayer">

            </div>
            <div class="navSelections">
                <i class="fa-solid fa-bars"></i>
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
    flex-direction: row;
    justify-content: space-between; 
    align-items: center;
    
    /* width: 200px; */
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
    display: inline;
    height: 10px;
    transition: height;;
    transition-duration: 0.5s;
    /* background-color: #fff; */
}
.fa-solid.fa-bars:focus ~ .navSelectionsMenu{
    display: inline;
    height: 30px;
    transform: translate(0px, -10px);
    transition: transform 0.5s;
    background-color: rgb(0, 0, 255);
}
/* 切换css样式 */
.navSelections{
} 

@media screen and (max-width: 481px){
    .nav_font{
        display: none;
    }
    .fa-solid.fa-bars{
        font-size: 50px;
        display: inline;
    }
}
</style>