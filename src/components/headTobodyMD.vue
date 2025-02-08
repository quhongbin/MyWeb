<script>
export default {
    data(){
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
    },
    mounted(){
    },
    components:{
    }
}
</script>


<template>
    <div>
        <input type="file" @change="uploadMarkdown" accept=".md" value=""/>
    </div>
</template>

<style scoped>
    div{
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 20px 20px;
        /* background-color: rgba(245, 245, 245, 0.7); */
    }
</style>