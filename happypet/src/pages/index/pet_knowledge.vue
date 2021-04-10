<template>
<view class="content" style="display:flex;align-items:center;flex-direction:column">

    <view class="example-body">
        
        <uni-search-bar radius="100" placeholder="自定义圆角" @confirm="search" />
    </view>

    <view class="table-section" style="height:50px;width:100%">
        <ul class="table-ul" style="width:100%">
            <li>常识</li>
            <li>疾病</li>
            <li>护理</li>
            <li>喂养</li>
            <li>驯养</li>
        </ul>
        
    </view>

    <view class="hot-search2" style="height:100%;width:100%">
        <view class="block" style="position:relative;height:150px;width:95%;background-color:green;margin:5px;margin-bottom:10px;border-radius:20px;box-shadow:1px 2px 3px 4px #ccc ;" v-for="index of 5">
            <img class="img" src="../../static/knowledge/1.png" style="width:100%;height:100%;position:relative;border-radius:20px">
                                <view class="block-word" style="position:absolute;left:20px;top:20px;font-size:20px;color:white">狗狗会经常露出肚皮么？</view>
                                <view class="bolck-view" style="position:absolute;left:200px;top:115px;color:white">500浏览</view>
                                <view class="block-use" style="position:absolute;left:300px;top:115px;color:white">10有用</view>

            </img>

            
        </view>
        
    </view>
</view>



</template>

<script>
export default {
    

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

</style>