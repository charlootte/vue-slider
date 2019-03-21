<template>
    <div class="slider-wrapper">
        <ul class="img-wrapper clearfix">
            <li class="slider-item f-l" v-for="(i,index) in imgList" :key="i.id"
                :class="[index == activeIndex  ? 'active-item' : (index<activeIndex ? 'to-left':'to-right')]">
                <img :src="require('../assets/img/pictureflow/'+i.name)" alt="i.name">
            </li>
        </ul>
        <i class="arrow left-arrow" v-on:click="goLast"></i>
        <i class="arrow right-arrow" v-on:click="goNext"></i>
    </div>
</template>

<script>

    export default {
        name: "Slider",
        props:['pid'],
        data(){
            return{
                imgList:[
                    {id:'1',name:'1.jpg'},
                    {id:'2',name:'2.jpg'},
                    {id:'3',name:'3.jpg'},
                    {id:'4',name:'4.jpg'},
                    {id:'5',name:'5.jpg'},
                    {id:'6',name:'6.jpg'},
                    {id:'7',name:'7.jpg'},
                    {id:'8',name:'8.jpg'},
                    {id:'9',name:'9.jpg'},
                    {id:'10',name:'10.jpg'},
                    {id:'11',name:'11.jpg'},
                    {id:'12',name:'12.jpg'},
                    {id:'13',name:'13.jpg'},
                    {id:'14',name:'14.jpg'},
                    {id:'15',name:'15.jpg'},
                    {id:'16',name:'16.jpg'},
                    {id:'17',name:'17.jpg'},
                ],
                activeIndex:'',
            }
        },
        mounted:function(){
            let self = this;
            self.imgList.find((val,index,arr)=>{
                if(val.id == self.pid){
                    self.activeIndex = index;
                }
            })
        },
        methods:{
            goLast:function(){
                let active = this.activeIndex;
                if(active>0){
                    this.activeIndex = --this.activeIndex;
                }
            },
            goNext:function() {
                let active = this.activeIndex;
                if (active < (this.imgList.length-1)) {
                    this.activeIndex = ++this.activeIndex;
                }
            },
        },

    }
</script>

<style scoped>
    .slider-wrapper{
        position: fixed;
        top:0;
        bottom:0;
        width:100%;
    }
    .img-wrapper{
        height:100%;
        width:100%;
        overflow: hidden;
        background-color:rgba(0,0,0,.7);
    }
    .slider-item{
        position:absolute;
        left: 50%;
        margin:0 30px;
        height:100%;
        transition: all 1s ease;
    }
    .slider-item img{
        height:100%;
    }
    .active-item{
        transform:translate(-50%,0);
    }
    .to-left{
        transform: translate(-2000px,0);
    }
    .to-right{
        transform: translate(2000px,0);
    }
    .arrow{
        position: absolute;
        top:45%;
        display: inline-block;
        width:128px;
        height:128px;
        cursor: pointer;
    }
    .left-arrow{
        left:10px;
        background:url(../assets/img/left.png) center no-repeat;
        background-size:100%;
    }
    .right-arrow{
        right:10px;
        background:url(../assets/img/right.png) center no-repeat;
        background-size:100%;
    }
</style>