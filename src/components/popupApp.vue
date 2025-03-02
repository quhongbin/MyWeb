<script>
export default {
    data(){
        return {
            icons:[
                {
                    icon: "fa-brands fa-github",
                    name: "Github",
                },
                {
                    icon: "fa-brands fa-bilibili",
                    name: "Bilibili",
                },
                {
                    icon: "fa-solid fa-envelope",
                    name: "邮箱",
                },
            ],
        };
    },
};
</script>
<template>
    <div class="popupMenu">
        <div v-for="(item,index) in icons" :key="index" class="popup-menu-items">
            <div>
                <i :class="item.icon"></i>
                {{ item.name }}
            </div>
        </div>
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
    background-color: rgba(193, 193, 193, 0.9);
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
</style>