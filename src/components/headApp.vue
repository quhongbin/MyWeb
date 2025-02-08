<script>
export default {
    data(){
        return{
            Markdowncontent: "",
        };
    },
    // methods: {
    //     uploadMarkdown(e){
    //         const file = e.target.files[0];
    //         if(file){
    //             var reader = new FileReader();
    //             reader.onload = (e) => {
    //                 this.$emit("MarkdownContentToBody", e.target.result);
    //             };
    //             reader.readAsText(file);
    //         };
    //     },
    // },
    mounted(){
    },
    components:{
    }
}
</script>
<template>
    <div class="nav_container">
        <div class="nav_logo">
            <img src="../assets/images/qq头像.jpg" alt="logo" width="50px" height="50px"/>
        </div>
        <div class="nav_font">
            <div>Github</div>
            <div>Bilibili</div>
            <div>Email</div>
        </div>
        <div class="nav__menu">
            
        </div>

    </div>
</template>

<style scoped>
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
    align-items: center;
    width: 200px;
}
</style>