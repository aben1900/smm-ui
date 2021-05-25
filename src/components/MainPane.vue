<template>
  <div style="font-family:'微软雅黑';" >
    <el-tabs v-model="mainActiveName" @tab-click="handleClick">
      <el-tab-pane label="主页面" name="firstMainTab" class="el_tabs">
          <div class="el_header">
            <div><label style="font-size: 40px;">来吧，让我们为梦想窒息! </label>
              <el-tooltip style="color:darkred;" class="item" effect="light" placement="right-start">
                <div slot="content" class="notes-class" style="font-size: 10px;">
                  游戏规则:
                  <br/>
                  (1)投资1分钱<br>(2)选择所在地区,选择服务类型,填写需要的内容<br>(3)提交<br>(4)看排队，每凑齐对应的金额，实现一个梦想<br>
                  (5)说不定就能完成自己的小梦想<br><font color="blue">注：商品还是要量力而行，如果太不合理可能会被其他人投票下线</font>
                </div>
                <i class="el-icon-question" style="font-size: 20px;"/>
              </el-tooltip>
            </div>
            <span style="margin-bottom:10px;color:darkred;">凑钱提要求，实现梦想，先提先实现，大伙一起玩！</span>
          </div>
          <div class="el_main">
            <img alt="Vue logo" src="../assets/logo.jpg" width="200">
            <div>当前的凑钱余额:¥ <span style="color:darkred;">0.01</span></div>
            <div>待实现的梦想商品/服务数量: <span style="color:darkred;">3</span> 个</div>
            <div>
              <label>选择所在地区 </label>
              <el-cascader clearable
                           size="large"
                           :options="regionOptions"
                           v-model="needRegions"
                           @change="handleChange">
              </el-cascader>
              <el-select v-model="needTypeValue" placeholder="请选择梦想类型" clearable>
                <el-option-group
                    v-for="group in needTypeOptions"
                    :key="group.label"
                    :label="group.label">
                  <el-option
                      v-for="item in group.options"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                  </el-option>
                </el-option-group>
              </el-select>
              <el-input style="width:400px;" placeholder="倔强的留下点信息" v-model="donatename"></el-input>
              <el-button @click="confirmDonate">已投资确认</el-button>
              <!--          <iframe id="reportFrame" width="900" height="400" src="https://fanruan.smec-cn.com/webroot/decision/v10/entry/access/854bcc17-c1c6-4042-b70c-cc2ce28b79b3?preview=true&hth=Y1001&__pi__=true"></iframe>-->
            </div>
<!--            <div class="bind">-->
              <!--      <div>绑定值：{{selectedOptions}}</div>-->
              <!--      <div>区域码转汉字：{{CodeToText[selectedOptions[0]]}},{{CodeToText[selectedOptions[1]]}},{{CodeToText[selectedOptions[2]]}}</div>-->
              <!--      <div>汉字转区域码：{{convertTextToCode(CodeToText[selectedOptions[0]], CodeToText[selectedOptions[1]], CodeToText[selectedOptions[2]])}}</div>-->
<!--            </div>-->
          </div>

          <div class="el_footer">
           <ListTabs></ListTabs>
          </div>

      </el-tab-pane>
      <el-tab-pane label="工具页面" name="secondMainTab">配置管理</el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import {
  provinceAndCityData,
  regionData,
  provinceAndCityDataPlus,
  regionDataPlus,
  CodeToText,
  TextToCode
} from 'element-china-area-data'
import ListTabs from './ListTabs'

export default {
  name: "MainPane",
  components:{
    ListTabs
  },
  data() {
    return {
      mainActiveName: 'firstMainTab',
      CodeToText,
      TextToCode,
      regionOptions: regionData,
      needRegions: [],
      dreamTemp: this.dreamData,
      donatename: '',
      needTypeOptions: [
        {
          label: '1分钱的服务',
          options: [{
            value: 'Chengdu',
            label: '表白'
          }, {
            value: 'Shenzhen',
            label: '拒绝'
          }, {
            value: 'tucao',
            label: '吐槽'
          }, {
            value: 'daoqiang',
            label: '道歉'
          }, {
            value: 'houhui',
            label: '后悔'
          }, {
            value: 'Dalian',
            label: '真心话大冒险'
          }]
        }
        , {
          label: '商品',
          options: [{
            value: 'Buy',
            label: '买东西(请提供链接)'
          }, {
            value: 'FreeGive',
            label: '送东西(舍不得丢的东西)'
          }]
        }],
      needTypeValue: '',

    }
  },
  mounted() {
    this.printout()
  },
  methods: {
    handleChange(value) {
      console.log(value)
    },
    confirmDonate() {
      // if (this.selectedOptions.length === 0) {
      //   this.$message.warning('请确认具体省市，出钱后总要出个响声.')
      //   return
      // }


      let url = 'https://fanruan.smec-cn.com/webroot/decision/v10/entry/access/854bcc17-c1c6-4042-b70c-cc2ce28b79b3?preview=true&hth=Y1001&__pi__=true'
      var username = document.getElementById("username"); //获取输入的用户名
      var password = document.getElementById("password");  //获取输入的参数
      var scr = document.createElement("iframe");      //创建iframe
      username = 'admin'
      scr.src = "https://fanruan.smec-cn.com/webroot/decision/v10/entry/access/854bcc17-c1c6-4042-b70c-cc2ce28b79b3?preview=true&hth=Y1001&__pi__=true" + encodeURIComponent(username)
      this.$confirm('确认后不能修改，请仔细校对文字及内容!')
          .then(() => {

          }).catch(err => {
        console.log(err)
      })
      console.log(this.selectedOptions)
    },
    printout() {
      // console.log(provinceAndCityData)
      // console.log(regionData)
      // console.log(provinceAndCityDataPlus)
      // console.log(regionDataPlus)
      // console.log(CodeToText)
      // console.log(TextToCode)
    },
    convertTextToCode(provinceText, cityText, regionText) {
      let code = "";
      if (provinceText && this.TextToCode[provinceText]) {
        const province = this.TextToCode[provinceText];
        code += province.code + ", ";
        if (cityText && province[cityText]) {
          const city = province[cityText];
          code += city.code + ", ";
          if (regionText && city[regionText]) {
            code += city[regionText].code;
          }
        }
      }
      return code;
    },

    handleClick(tab,event){

    }
  }
}
</script>

<style scoped>
.notes-class {
  line-height: 25px;
  font-size: 40px;
}

/*.el-tabs >>> .el-tabs__content{*/
/*  height: 100%;*/
/*}*/

.el_tabs{
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
}
.el_header{
  height: 100%;
}
.el_main{
  height: 100%;
}

.el_footer{
  flex: 2;
  height: 100%;
}
</style>
