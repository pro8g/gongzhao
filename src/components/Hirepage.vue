<script setup>
import { reactive } from 'vue'
import HireItem from './Hirepage/HireItem.vue'
import Header from './Header.vue'
defineProps({
  msg: String,
})

const state = reactive({
  // keyword: route.query.keyword || '',
  nowhiringList:[
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    },
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    },
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    },
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    },
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    },
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    },
    {
      name: '行政文员',
      category: 8801,
      organization: '广州市白云区数据管理局',
      base: '广州',
      labels: ['正式编制','18-35','大专','退役军人优先','线上报名','仅面试'],
      majorCode: ['电子信息类'],
    }
  ],
  totalnumber: 0,
  city: 0,
  loading: false,
  finished: false,
  orderby: ''
})
const init = async () => {
  
}
</script>

<template>
  <div class="item-list-wrap">
    <Header />
    <div class="item-list-content">
      <div  class="item-list-item">
        <ul class="list-none text-black pl-0 bg-zinc-100">
          <HireItem v-for="(item, index) in state.nowhiringList" :key="index" :item="item" />
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
