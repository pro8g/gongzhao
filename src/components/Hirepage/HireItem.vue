<template lang="">
    <li class="item my-[4px] bg-white px-5 py-4">
        <a class="text-black ">
            <div class="title flex justify-between">
                <span class="title-text text-xl">{{item.name}}</span>
                <span class="category text-rose-600">{{categorytext}}</span>
            </div>
            <div class="info flex mb-2">
                <span class="workspace text-slate-400">{{item.base}}</span>
            </div>
            <div class="labels flex flex-wrap mb-3">
                <span class="label bg-slate-100 rounded-full px-1.5 py-0.5 mr-1.5 mb-1.5 text-xs text-slate-600" v-for="(label,index) in item.labels" :key="index">{{label}}</span>
                <span class="label bg-slate-100 rounded-full px-1.5 py-0.5 mr-1.5 mb-1.5 text-xs text-slate-600" v-if="!item.majorCode || item.majorCode.length === 0">三不限</span>
                <span class="label bg-slate-100 rounded-full px-1.5 py-0.5 mr-1.5 mb-1.5 text-xs text-slate-600" v-for="(major,index) in item.majorCode" :key="index">{{major}}</span>
            </div>
            <div class='organization flex justify-between text-sm'>
                <span class="organization-text leading-8">{{item.organization}}</span>
                <div class="button-detail bg-cyan-400 rounded-full text-white w-[100px] h-[30px] text-center leading-8">查看详情</div>
            </div>            
        </a>
    </li>
</template>
<script>
export default {
    props:{
        item:{
            name: String,
            category: 0,
            organization: String,
            base: String,
            labels: [],
            majorCode: []
        }
    },
    computed:{
        categorytext(){
            switch (this.item.category) {
                case 8801:
                    return '聘用制';
                case 8802:
                    return '见习岗位';
                case 8803:
                    return '事业单位';
                case 8804:
                    return '公务员';
                case 8805:
                    return '政府雇员';
                default:
                    return '';
            }
        }
    }
}

</script>
<style lang="">
    
</style>