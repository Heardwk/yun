<template>
  <div class="feight">
    <div v-if="allcase.thirdrouter" class="componentBox">
      <p class="path">
        <router-link to="/Teacher/Shixun">实训中心</router-link> &gt;
        <router-link to="/Teacher/Shixun/Course">{{bookName}}</router-link> &gt;
        全真案例
      </p>
      <div class="contentBox">
        <div class="contentLeft">
          <p>
            <span class="hasLine">知识点</span>
            <el-input
              class="serch"
              placeholder="关键字搜索"
              v-model="filterText">
            </el-input>
            <el-tree
              class="tree"
              :props="defaultProps"
              :data="dataList"
              node-key="id"
              ref="tree"
              :filter-node-method="filterNode"
              accordion>
            </el-tree>
          </p>
        </div>
        <div class="contentRight">
          <p style="position: relative">
            <span class="hasLine">案例列表</span>
            <router-link to="/Teacher/Shixun/Course/allTrueCase/pubMission" class="pubmis"><span class="el-icon-circle-plus"></span>发布任务</router-link>
          </p>
          <div class="choooseContent">
            <ul class="titleUlBox">
              <li>
                <span class="num">序号</span>
                <span class="name">案例名称</span>
                <span class="type">题型</span>
                <span class="count">练习次数</span>
              </li>
              <li v-for="(item,index) in topicData" class="titltLi">
                <span class="num">{{index+1}}</span>
                <span class="name">{{item.name}}</span>
                <span class="type">{{item.type}}</span>
                <span class="count">{{item.count}}</span>
              </li>
            </ul>
            <div style="text-align: right; margin-bottom:20px;">
              <el-pagination
                background
                layout="prev, pager, next"
                @current-change="changePage"
                :total="50">
              </el-pagination>
            </div>
          </div>
        </div>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'allTrueCase',
  data () {
    return {
      bookName: '',
      defaultProps: {
        label: 'label',
        children: 'children'
      },
      dataList: [
        {
          id: 1,
          label: '一级 1',
          children: [{
            id: 4,
            label: '二级 1-1',
            children: [{
              id: 9,
              label: '三级 1-1-1三级'
            }]
          }]
        }, {
          id: 2,
          label: '一级 2',
          children: [{
            id: 5,
            label: '二级 2-1',
          }, {
            id: 6,
            label: '二级 2-2',
            children: [{
              id: 11,
              label: '三级 2-2-1'
            }]
          }]
        }, {
          id: 3,
          label: '一级 3',
          children: [{
            id: 7,
            label: '二级 3-1',
            children: [{
              id: 12,
              label: '三级 3-1-1'
            }]
          }, {
            id: 8,
            label: '二级 3-2',
            children: [{
              id: 13,
              label: '三级 3-2-1'
            }]
          }]
        }
      ],
      filterText: '',
      topicData: [
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
        {
          name: '提供的原始单据、记账凭证、账薄资料等,要求选用正确的方法AAbb',
          point: '基础会计',
          type: '单选题',
          count: 2,
          chec: false
        },
      ],
    }
  },
  mounted() {
    this.$store.commit("secondrouterCtrl",false);
    this.bookName = localStorage.getItem("bookName");
  },
  computed: {
    allcase() {
      return this.$store.state
    },
  },
  watch: {
    filterText(val) {
      this.$refs.tree.filter(val);
    }
  },
  methods: {
    filterNode(value, data) {
      if (!value) return true;
      return data.label.indexOf(value) !== -1;
    },
    changePage(){

    },
  },
  destroyed() {
    this.$store.commit("secondrouterCtrl",true)
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .path {
    color: #687178;
    font-size: 16px;
    margin-top: 40px;
    margin-bottom: 20px;
  }
  .contentBox {
    position: relative;
  }
  .contentLeft {
    position: absolute;
    top: 0;
    left: 0;
    width: 255px;
    height: 720px;
    background-color: white;
    padding: 20px;
    border-radius: 4px;
    font-size: 14px;
  }
  .contentLeft .el-input {
    display: inline-block;
    width: 135px;
    font-size: 12px;
    margin-left: 30px;
  }
  .tree {
    margin-top: 10px;
    height: 530px;
    overflow-y: auto;
    white-space: nowrap;
    overflow-x: hidden;
    text-overflow: ellipsis;
  }
  .hasLine {
    color: #243847;
    position: relative;
    padding: 0 0 10px 0;
  }
  .hasLine::after {
    content: '';
    position: absolute;
    bottom: 4px;
    left: 0;
    width: 100%;
    height: 4px;
    background-color: #00B0FF;
    border-radius: 11px;
  }
  .pubmis {
    position: absolute;
    right: 0;
    color: #243847;
    font-size: 12px;
    cursor: pointer;
    line-height: 28px;
    padding-left: 35px;
  }
  .pubmis:hover {
    color: #F77676;
  }
  .pubmis span {
    font-size: 28px;
    color: #00B0FF;
    position: absolute;
    left: 0px;
  }
  .pubmis:hover span {
    color: #F77676;
  }
  .contentRight {
    margin-left: 275px;
    padding: 20px;
    font-size: 14px;
    background-color: white;
    border-radius: 4px;
    height: 770px; 
  }
  .err {
    position: relative;
    margin-top: 20px;
    min-height: 40px;
    line-height: 35px;
  }
  .err>span {
    color: #6E768F;
    font-size: 18px;
    position: absolute;
  }
  .err p {
    margin-left: 100px;
  }
  .err p span {
    margin-right: 10px;
  }
  .screen {
    position: relative;
    margin-top: 8px;
    min-height: 25px;
    line-height: 22px;
    font-size: 12px;
  }
  .screen:first-child { 
    margin-top: 20px;
  }
  .screen .scrType {
    position: absolute;
    color: #00B0FF;
    width: 55px;
    text-align: right;
  }
  .screen p {
    margin-left: 60px;
  }
  .screen p span {
    margin-right: 8px;
    cursor: pointer;
  }
  .screen p span:hover {
    color: #00B0FF;
  }
  .choooseContent {
    position: relative;
    min-height:350px;
    margin-top: 20px;
  }
  .chooseBox {
    height: 530px;
    overflow-x: hidden;
    overflow-y: auto;
  }
  .titleUlBox {
    font-size: 12px;
    color: #42424E;
    padding: 0;
  }
  .titleUlBox li:first-child {
    background-color: #EFEFF4;
    margin-bottom: 5px;
  }
  .titltLi {
    background-color: #FBFBFB;
  }
  .titltLi:nth-child(2n) {
    background-color: #EFEFF4;
  }
  .titltLi:hover {
    background-color: #FEF1F1;
  }
  .titleUlBox li span {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    height: 40px;
    line-height: 40px;
  }
  .titleUlBox .num {
    display: inline-block;
    width: 55px;
    text-align: center;
  }
  .titleUlBox .name {
    display: inline-block;
    width: 430px;
    text-align: center;
  }
  .titltLi .name {
    text-align: left;
  }
  .titleUlBox .type {
    display: inline-block;
    width: 75px;
    text-align: center;
  }
  .titleUlBox .count {
    display: inline-block;
    width: 65px;
    text-align: center;
  }
</style>
