<template lang="">
    <div>
        <div id='header overflow-y-auto relative'>
            <div class='search-bar'>
               <div class='top-search'>
                  <div class="search-list-wrap ">
                     <ul class="search-list-title list-none pl-0">
                        <li class='get-position-box' @click="positionClick">定位</li>
                        <li @click="iscityboxhidden = false">城市</li>
                        <li @click="showExperience">经验</li>
                        <li @click="showEducation">学历</li>
                        <li @click="showJobType">职务类型</li>                        
                     </ul>
                     <div class="filter-content fixed inset-x-0 w-full bg-grey-100 ">
                        <ul class="">
                           <li class="experiance-bar w-full bg-white" v-show="experianceshow">
                              <ul class="">
                                 <li class="" v-for="item in filtercontent.experence">
                                    <a class="pl-5 text-balck">{{item}}</a>
                                 </li>
                              </ul>
                           </li>
                           <li class="edcuation-bar w-full bg-white" v-show="eductionshow">
                              <ul  class="">
                                 <li class="" v-for="item in filtercontent.education">
                                    <a class="pl-5 text-black">{{item}}</a>
                                 </li>
                              </ul>
                           </li>
                           <li class="jobtype-bar w-full bg-white" v-show="jobtypeshow">
                              <ul class="">
                                 <li class="" v-for="item in filtercontent.jobtype">
                                    <a class="pl-5 text-black">{{item}}</a>
                                 </li>
                              </ul>
                           </li>
                        </ul>
                     </div>
                     <div class="city-box-container flex flex-wrap bg-white fixed max-h-screen top-0 left-0" :class="{hidden : iscityboxhidden}">
                        <a class="city-closebox w-1/2 h-[30px]" @click="iscityboxhidden = true">X</a>
                        <a class="citynow w-1/2 h-[30px]">广州</a>
                        <div class="city-box w-1/2 h-full">
                           <div class="scroller">
                              <ul class="list-none pl-0">
                                 <li v-for="(city, index) in cities" @click="showSubs(city)">
                                    {{ city.name }}
                                 </li>
                              </ul>
                           </div>
                        </div>
                        <div class="city-child-box w-1/2 h-full overflow-y-auto">
                           <div class="scroller">
                              <ul class="">
                                 <li class="" v-for="sub in currentSubs.showsubs">{{sub}}</li>
                              </ul>
                           </div>
                        </div>
                     </div>
                  </div>
                  <div class="message-wrap">
                     <div class="message-icon"></div>

                  </div>
               </div>
            </div>
            <div class="filter-bar-wrap">
               <div class="city-selector city-text"></div>
               <div class="filter-bar filter-bar-new"></div>
            </div>
         </div>
    </div>
</template>
<script setup>
import { ref } from "vue";
const cities = [
    {
        name: '热门城市',
        index: 0,
        subs:['全国','北京','广州','深圳','上海','天津','重庆','杭州','南京','武汉','西安','成都','厦门','长沙','苏州','天津','郑州','青岛','济南','石家庄','哈尔滨','大连','沈阳','长春','福州','厦门','南昌','贵阳','南宁','呼和浩特','乌鲁木齐','拉萨','兰州','西宁','银川','乌鲁木齐','石家庄','呼和浩特','乌鲁木齐','拉萨','兰州','西宁','银川','乌鲁木齐','石家庄','呼和浩特','乌鲁木齐','拉萨','兰州']
    },
    {
        name:'广东',
        index: 1,
        subs:['广州', '深圳', '珠海', '汕头', '韶关', '佛山', '江门', '湛江', '茂名', '肇庆', '惠州', '梅州', '汕尾', '河源', '阳江', '清远', '东莞', '中山', '潮州', '揭阳', '云浮']
    }
]
const filtercontent = 
   {
      experence: ['不限', '1年以下', '1-3年', '3-5年', '5-10年'],
      education: ['不限', '小学', '大专', '本科', '硕士', '博士'],
      jobtype: ['合同制', '政府雇员', '事业编制', '见习', '公务员', '兼职/实习']
   }
const iscityboxhidden = ref(true)
const experianceshow = ref(false)
const jobtypeshow = ref(false)
const eductionshow = ref(false)
const showExperience = () => {
   experianceshow.value = !experianceshow.value
   jobtypeshow.value = false
   eductionshow.value = false
}
const showEducation = () => {
   eductionshow.value = !eductionshow.value
   experianceshow.value = false
   jobtypeshow.value = false
}
const showJobType = () => {
   jobtypeshow.value = !jobtypeshow.value
   eductionshow.value = false
   experianceshow.value = false
}
const currentSubs = ref({
   showsubs: cities[0].subs,
   show: true
})

const positionClick = () => {
    navigator.geolocation.getCurrentPosition((res) => {
        console.log(res)
    },err => {
        console.log(err)
    },{
        enableHighAccuracy: true,
        timeout: 5000,
        maximumAge: 0
    }
    )
}
const showSubs = (city) =>  {
   currentSubs.value.showsubs = city.subs;
}

</script>
<style lang="css">
    .search-bar .search-list-wrap {
        width: 100%;
        z-index: 1;
    }
    .search-list-title li{
      width: 15%;
      display: inline-block;
      font-size: 13px;
    }
    .city-box-container {
      width: 100%;
      height: 100vh;
      
    }
    ul {
      list-style-type: none;
      padding-left: 0px;
    }
    .scroller ul>li {
      height: 60px;
      line-height: 60px;
    }
    li>ul>li {
      height: 60px;
      line-height: 60px;
    }

</style>