# 1.前端实用方法

## 1.1iview+table+page表格分页功能

```vue
<template>
  <div>
    <Table :columns="historyColumns" :data="historyData"></Table>
    <Page :page-size-opts=[5,10,15] :total="dataCount" @on-page-size-change="changePageSize" :page-size="pageSize" show-total class="paging" @on-change="changepage" show-sizer></Page>
  </div>
</template>
<style scoped>
.paging{
  float:right;
  margin-top:10px;
}
</style>
<script>
let testData = {
  "histories": [
    {
      "username": "智能审批",
      "shenpistatus": "审批已通过",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-24 18:11"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批已通过",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-24 18:11"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批已通过",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-24 10:04"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201",
      "time": "2017-07-24 10:03"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201",
      "time": "2017-07-24 10:02"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批已通过",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-24 10:02"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-24 10:01"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-24 09:56"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:23"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-21 14:23"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:23"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-21 14:23"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-21 14:23"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-21 14:21"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:21"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:20"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-21 14:20"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:14"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:13"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:11"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-21 14:10"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-20 18:09"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-20 18:08"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "  收入 > 999 && 支出 < 201 && 所有项目的总净收入 > 5000",
      "time": "2017-07-20 18:08"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-20 18:07"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-20 18:05"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批已通过",
      "shenpicomments": "wedfqw",
      "time": "2017-07-20 15:50"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批已通过",
      "shenpicomments": "wedfqw",
      "time": "2017-07-20 15:20"
    },
    {
      "username": "智能审批",
      "shenpistatus": "审批被拒绝",
      "shenpicomments": "自动审批通过",
      "time": "2017-07-19 18:27"
    }
  ]
}
export default {
  data () {
    return {
      ajaxHistoryData:[],
      // 初始化信息总条数
      dataCount:0,
      // 每页显示多少条
      pageSize:5,
      historyColumns: [
        {
          title: '人员',
          key: 'username'
        },
        {
          title: '操作',
          key: 'shenpistatus'
        },
        {
          title: '意见',
          key: 'shenpicomments'
        },
        {
          title: '时间',
          key: 'time'
        }

      ],
      historyData: []
    }
  },
  methods:{
    // 获取历史记录信息
    handleListApproveHistory(){

      // 保存取到的所有数据
      this.ajaxHistoryData = testData.histories
      this.dataCount = testData.histories.length;
      // 初始化显示，小于每页显示条数，全显，大于每页显示条数，取前每页条数显示
      if(testData.histories.length < this.pageSize){
        this.historyData = this.ajaxHistoryData;
      }else{
        this.historyData = this.ajaxHistoryData.slice(0,this.pageSize);
      }


    },
    changepage(index){
      var _start = ( index - 1 ) * this.pageSize;
      var _end = index * this.pageSize;
      this.historyData = this.ajaxHistoryData.slice(_start,_end);
    },
    changePageSize(count){

      console.log(count)
      this.pageSize = count
      this.handleListApproveHistory()
    }
  },
  created(){
    this.handleListApproveHistory();
  }
}
</script>
```

# 2.前端实用组件
## 2.1 vue无缝滚动组件 vue2 https://chenxuan0000.github.io/vue-seamless-scroll/  vue3 https://doc.wssio.com/opensource/vue3-seamless-scroll/#%E5%BC%80%E5%A7%8B
## 2.2 vue-cropper 裁剪图片插件 https://github.com/xyxiao001/vue-cropper
# 3.前端实用网址
## 3.1 echarts库 http://echarts.zhangmuchen.top/#/index
## 3.2 css边框样式生成器 https://9elements.github.io/fancy-border-radius/#35.100.76.0--.
## 3.3 css动画生成器 https://animista.net/ https://angrytools.com/css/animation/
## 3.4 自定义形状分隔线 [https://www.shapedivider.app/](https://link.zhihu.com/?target=https%3A//www.shapedivider.app/)
## 3.5 前端知识网址 https://www.kwgg2020.com/
