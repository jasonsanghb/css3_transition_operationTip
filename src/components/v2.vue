<template>
    <div>
        <div class="container" ref="container">
            <div class="title" ref="title">
                操作提示
                <span class="icon" @click="close" v-show="show">&times;</span>
                <span class="icon" @click="open" v-show="!show">&gt;&gt;</span>
            </div>
            <div class="body" ref="body">
                <p>一：媕娿五年内放哪里舒服new</p>
                <p>二：阿为了你拉文你</p>
                <p>三：啊诶偶然翻围殴内容</p>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "v2",
    data() {
      return {
        show:true,
        prevWidth:'',
        prevHeight:''
      }
    },
    methods:{
      close(){
        this.prevWidth = this.getStyle(this.$refs.container, 'width')
        this.prevHeight = this.getStyle(this.$refs.container, 'height')
        this.$refs.container.style.height = this.prevHeight
        this.show = false
        this.$refs.container.style.height = this.$refs.title.offsetHeight + 'px'
        setTimeout(()=>{
          this.$refs.container.style.width = 150 + 'px'
        },1000)

      },
      getStyle(obj, attr) {
        if(obj.currentStyle) {
          return obj.currentStyle[attr];}
        else {
          return getComputedStyle(obj, false)[attr];
        }
      },
      open(){
        this.$refs.container.style.width = this.prevWidth
        setTimeout(()=>{
          this.$refs.container.style.height = this.prevHeight
        },1000)
      }
    }
  }
</script>

<style scoped lang="scss">

    .container{
        position: relative;
        width: 800px;
        border: 1px dashed blue;
        padding: 15px 25px;
        transition: all 1s ease;
        overflow: hidden;
        .title{
            position: relative;
            padding: 10px;
            .icon{
                position: absolute;
                top:0;
                right:0;
                font-size: 20px;
                font-weight: 900;
                color: #ccc;
                &:hover{
                    cursor: default;
                    color: #000;
                }
            }

        }
    }
</style>
<style lang="scss">
    /*html,body,#app{*/
    /*    margin: 0;*/
    /*    padding: 0;*/
    /*}*/
</style>
