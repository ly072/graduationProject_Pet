<template>
<view class="content" style="display:flex;align-items:center;flex-direction:column">

    <view style="width:100%">
        
        <uni-search-bar radius="100" placeholder="你想要的知识都在这～" @confirm="search" />
    </view>

    <view class="table-section" style="height:50px;width:100%">
        <ul class="c-ul" style="width:100%">
            <li style="font-size:20px">全部</li>
            <li>常识</li>
            <li>疾病</li>
            <li>护理</li>
            <li>喂养</li>
            <li>驯养</li>
        </ul>
        
    </view>

    <view class="hot-search2" style="height:100%;width:100%">
        <view class="block" style="position:relative;height:150px;width:95%;background-color:green;margin:5px;margin-bottom:10px;border-radius:20px;box-shadow:1px 2px 3px 4px #ccc ;" v-for="(item,index) in knowledge_img">
            <img class="img" :src="knowledge_img[index].src" style="width:100%;height:100%;position:relative;border-radius:20px">
                                <view class="block-word" style="position:absolute;left:20px;top:20px;font-size:20px;color:white">{{knowledge_item_word[index]}}</view>
                                <view class="bolck-view" style="position:absolute;left:200px;top:115px;color:white">500浏览</view>
                                <view class="block-use" style="position:absolute;left:300px;top:115px;color:white">10有用</view>

            </img>

            
        </view>
        
    </view>
</view>



</template>

<script>
export default {
            data(){
                return {

                                    knowledge_img:[
                {src:require('../../static/knowledge_1.png')},
                {src:require('../../static/knowledge_2.jpg')},
                {src:require('../../static/knowledge_3.png')},
                {src:require('../../static/knowledge_4.jpg')},
                {src:require('../../static/knowledge_5.jpg')}
            ],
                        knowledge_item_word:[
                "狗狗会经常露出肚皮么？",
                "什么会影响狗狗的发情周期？",
                "男生狗狗为啥会抬腿尿尿？",
                "给狗狗做检查的方法？",
                "狗狗绝育前需要做那些准备？"
            ]

                }
            },


    

    onLoad(){
console.log("create");
    },
    methods:{

    }
}
</script>


<style lang="scss" scoped>
.table-section ul li{
  list-style: none;
  margin-left:30px;
  display: inline;

}

.table-section ul{
    margin-top:15px;
    margin-left: -40px;
    margin-bottom:15px;

}

</style>