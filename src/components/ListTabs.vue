<template>
  <div class="list_tabs">
  <el-tabs  v-model="activeTabName" type="card" @tab-click="tabHandleClick" >
    <el-tab-pane label="已实现队列" name="first">
      <el-table
          class="tabs_table"
          stripe
          :data="dreamData" >
        <el-table-column
            prop="date"
            label="日期"
            width="180">
        </el-table-column>
        <el-table-column
            prop="name"
            label="称呼"
            width="180">
        </el-table-column>
        <el-table-column
            prop="address"
            label="地区">
        </el-table-column>
        <el-table-column
            prop="address"
            label="地区">
        </el-table-column>
      </el-table>
    </el-tab-pane>
    <el-tab-pane label="等待队列" name="second">配置管理</el-tab-pane>
    <el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
    <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
  </el-tabs>
  </div>
</template>

<script>
export default {
  name: "ListTabs",
  data() {
    return {
      activeTabName: 'first',
      dreamData: [
        {
          date: '2021-05-18 14:22:10',
          name: '蛋蛋',
          address: '上海市普陀区金沙江路 1518 弄',
          dtype: '商品',
          dname: '七巧板',
          detail: 'https://detail.tmall.com/item.htm?id=635121475044&ali_refid=a3_420434_1006:1110734000:N:+x9Y0Cedcv2KOR5hm6ZnJCta7zSjnxtC:3cb2890126b16d1874f268307685a571&ali_trackid=1_3cb2890126b16d1874f268307685a571&spm=a230r.1.1957635.2'
        },
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'},
        {date: '2016-05-04', name: '王小虎', address: '上海市普陀区金沙江路 1517 弄'}
      ],
    }
  },
  mounted() {
  },
  methods: {
    tabHandleClick(tab, event) {
      console.log(tab, event);
    }
  }
}
</script>

<style scoped>
/*.el-tabs >>> .el-tabs__content{*/
/*  height: 100%;*/
/*}*/
.list_tabs{
}
.tabs_table{
}
</style>
