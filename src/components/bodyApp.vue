<script>
import axios from "axios"
import markdownIt from "markdown-it"
import headTobodyMD from "./headTobodyMD.vue"
import popupApp from "./popupApp.vue"
import headApp from "./headApp.vue"
import EventBus from "./eventBus.vue"
import { ref } from "vue"

const markdowncontent=ref({})
export default {
  data() {
    return {
      // markdowncontent:{},
      isVisibleClass: false,
      tempText: {
        name: "瞿红斌",
        age:18,
        jianjie: "这是一个简介",
      },
      tags: [],
    };
  },
  props: {
    
    // Markdowncontent: {
    //   type: String,
    //   default: "",
    //   required: true
    // }
  },
  computed: {
    // updateMarkdown(){
    //     const md = new markdownIt();
    //     return md.render(this.Markdowncontent);
    // }
  },
  components: {
    headTobodyMD,
    popupApp,
    headApp
  },
  mounted() {
    // 监听switch-class事件，并执行toggleClass方法
    EventBus.on("switch-class", this.toggleClass);
  },
  beforeUnmount() {
    EventBus.off("switch-class",);
  },
  methods: {
    handleFileUploaded(newContent, fileName) {
      const md = new markdownIt();
      const fileContents = md.render(newContent);
      this.markdowncontent = newContent;
      // 增加一个div标签，用于显示新的内容
      // 将新的内容添加到tags数组中，并以文件名形式的变量名存储
      this.tags.push(fileContents);
      // this.$emit("addedContent");
      this.getToServer();
      console.log(fileName);
      console.log(markdowncontent);
      console.log(this.tags.length);
    },
    // axios请求
    getToServer() {
      axios.post("http://localhost:5000/api",
      {
        content:this.markdowncontent
      },{
        headers: {
          "Content-Type": "application/json",
        },
      }
      )
        .then((response) => console.log(response.data))
        .catch((error) => console.log("Error:"+error));
    },
    // 切换floatMenu的class样式
    toggleClass() {
      this.isVisibleClass = !this.isVisibleClass;
    },
    goToFooter() {
      this.$router.push("/Footer");
    },
  }
};

</script>
<template>

  <div class="bg-main">

    <!-- 左边内容 -->
    <div class="bg-left">
      <div class="bg-left-content">
        <div>
          <img src="../assets/images/qq头像.jpg" width="50px" height="50px" />
        </div>
        <div>
          <span>姓名：</span>
          <span>不知取啥</span>
        </div>
        <div>
          <span>简介：</span>
        </div>
      </div>
    </div>
    <!-- 左边内容 -->

    <!-- 中间内容 -->
    <div class="bg-center">
      <div class="bg-center-content">
        <div v-for="(item, index) in tags" :key="index">
          <div v-html="item">
          </div>
        </div>
        <div>
          <headTobodyMD @MarkdownContentToBody="handleFileUploaded" />
          <!-- <button @click="toggleClass">dd</button> -->
        </div>
      </div>
    </div>
    <!-- 中间内容 -->

    <!-- 右边内容 -->
     <div class="bg-right">
    </div>    




    <!-- 右边内容 -->

    <!-- 弹出框 -->
    <div :class="[isVisibleClass ? 'floatMenu' : 'floatMenuDisvisible']">
      <headApp style="display: none;"/>
      <popupApp :class="[isVisibleClass ?  'popupMenu' : 'popupMenuDisvisible']"></popupApp>
    </div>


    <!-- 弹出框 -->

  </div>
</template>

<style scoped>
@import url(../assets/css/animate.css);
.bg-center-content>::-webkit-scrollbar {
  width: 2px;
  /* 设置滚动条宽度为0 */
  height: 10px;
  /* 设置滚动条高度为0 */
  background-color: #f5f5f5;
  /* 设置滚动条背景颜色 */
  display: none;
  /* 隐藏滚动条 */
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(45deg, #888, #fff);
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.8);
}

.bg-main {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100%;
}

.bg-left {
  /* background-color: aqua; */
  display: inline-block;
  width: 20%;
  margin: 30px 0px 0 20px;
}

.bg-left-content {
  background-color: rgb(230, 230, 230);
  display: inline-flex;
  border: 2px solid rgb(115, 115, 115);
  border-radius: 20px;
  justify-content: space-around;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

.bg-left-content>div {
  margin: 10px 0px 10px 0px;
}

.bg-left-content img {
  border-radius: 20%;
}

/* 简介内容 */
.bg-left-content>div:nth-child(3) {
  height: 200px;
  width: 90%;
  word-wrap: break-word;
  /* overflow:scroll; */
  /* text-overflow:clip; */
}

/* 简介内容 */

/* 中间内容 */
.bg-center {
  display: inline-block;
  width: 65%;
  height: 200px;
  margin: 30px 0px 0 0px;
}

.bg-center-content>div {
  height: 200px;
  background-color: beige;
  margin: 5px 0px 10px 10px;
  padding: 0px 10px 0px 10px;
  border-radius: 20px;
  overflow: scroll;
  text-overflow: clip;
  transition-duration: 1s;
}
.bg-center-content>div:hover {
  transform: scale(1.05);
  transition: transform 0.5s;
}

/* 中间内容 */
/* 右边内容 */
.bg-right {
  display: inline-block;
  width: 15%;
  margin: 30px 20px 0 0px;
}

/* 右边内容 */
.floatMenuDisvisible {
  display: none;
}
.popupMenuDisvisible {
  display: none;
}
@media screen and (max-width: 481px){
    .bg-left{
        display: none;
    }
    .bg-center {
      display: inline-block;
      width: 100%;
      height: 200px;
      margin: 10px 0px 0 0px;
    }
    .bg-right{
        display: none;
    }
    .bg-center-content>div {
      height: 200px;
      background-color: beige;
      margin: 5px 10px 10px 10px;
      padding: 0px 10px 0px 10px;
      border-radius: 20px;
      overflow: scroll;
      text-overflow: clip;
    }
    .bg-center-content>div:hover {
      transform: none;
      transition: transform 0.5s;
    }
        /* 弹出框的消失样式 */
    .floatMenuDisvisible{
        position: fixed;
        display: inline-block;
        margin: 0px 0px 0px 50%;
        width: 80%;
        height: 100%;
        /* background-color: rgba(128, 128, 128, 0.7); */
        animation: LeftToRight 1s;
     }
    .popupMenuDisvisible {
        position: fixed;
        display: inline-block;
        margin: 0px 0px 0px 50%;
        width: 80%;
        height: 100%;
        /* background-color: rgba(128, 128, 128, 0.7); */
        animation: LeftToRight 1s;
    }
    /* 弹出框的消失样式 */

    /* 弹出框的出现样式 */
    .floatMenu {
      position:fixed;
      display: inline-block;
      margin: 0px 0px 0px 50%;
      width: 80%;
      height: 100%;
      /* background-color: rgba(204, 31, 31, 0.7); */
      animation: RightToLeft 0.5s;
    }
    .popupMenu {
      display: flex;
      width: 100%;
      height: 100%;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      /* padding: 10px 20px; */
      /* background-color: rgba(25, 255, 125, 0.7); */
      animation: RightToLeft 1s;
    }    
    /* 弹出框的出现样式 */
  }    

</style>
