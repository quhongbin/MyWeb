<script>
export default {
    data(){
        return {
            icons:[
                {
                name: 'Github',
                icon: 'fa-brands fa-github',
                url:'https://github.com/quhongbin',
                },
                {
                name: 'Bilibili',
                icon: 'fa-brands fa-bilibili',
                url:'https://space.bilibili.com/521816677',
                },
                {
                name: 'Email',
                icon: 'fa-solid fa-envelope',
                url:'mailto:2818777520@qq.com',
                },
            ],
        };
    },
    components:{
    },
};
</script>
<template>
    <div class="popupMenu">
        <div v-for="(item,index) in icons" :key="index" class="popup-menu-items">
            <div>
                <i :class="item.icon"></i>
                <a :href="item.url">{{ item.name }}</a>
            </div>
        </div>
        <span>
            <p>备案号：蜀ICP备2024111078号-1</p>
            <p>版权所有 &copy; 2023 quhongbin</p>
        </span>
    </div>
</template>
<style scoped>
@import url(../assets/fontawesome/fontawesome-free-6.7.2-web/css/all.css);
.popupMenu{
    display: flex;
    width: 100%;
    height: 100%;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    /* padding: 10px 20px; */
    background-color: rgba(255, 255, 255, 0.9);
}
.popup-menu-items{
    display: inline;
    justify-content: space-between;
    align-items: center;
    justify-content: center;
    width: 100%;
}
.popup-menu-items>div{
    margin: 20% auto auto 20%;
}
.popup-menu-items a{
    color: black;
    text-decoration: none;
}
.popup-menu-items a:active{
    color: red;
    text-decoration:line-through;
}
@media screen and (max-width: 481px) {
    span {
        display: inline;
        font-size: 8px;
        margin: 100% 50% auto auto;
    }
    
}
</style>