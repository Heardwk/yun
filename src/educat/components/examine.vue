<template>
	<div>
	  <div class="mission" v-if='examine.thirdrouter'>
	        <div class="tea_t">
    	        <el-breadcrumb separator-class="el-icon-arrow-right">
				  <el-breadcrumb-item :to="{ path: '/Educat/Teaching' }">任教管理</el-breadcrumb-item>
				  <el-breadcrumb-item :to="{ path: '/Educat/Teaching/taskdetail' }">任教详情</el-breadcrumb-item>
				  <el-breadcrumb-item>任务详情</el-breadcrumb-item>
			    </el-breadcrumb>
    	   </div>
    	    <div class="task_top">
    	       <p>{{data_list.name}}</p>
    	      <div calss="t_task">
    	       	  <ul class="t_task_t">
    	       	  	<li><b>开始时间:</b>:<span>{{data_list.fitime}}</span></li>
    	       	  	<li><b>结束时间:</b><span>{{data_list.endtime}}</span></li>
    	       	  	<li><b>参与班级:</b><span>{{data_list.tea_class}}</span></li>
    	       	  </ul>
    	       	  <ul class="t_task_t">
    	       	  	<li><b>分值:</b><span>{{data_list.grade}}</span></li>
    	       	  	<li><b>备注:</b><span>{{data_list.comments}}</span></li>
    	       	  </ul>
    	      </div>
    	   </div>
    	  <div class="tea_table">
    	   	 <div class="tea_table_top">
    	   	     <ul>
    	   	     	<li
    	   	     	v-for="(itemdata,index) in data" 
    	   	     	:key="index">
			          {{itemdata}}</li>
    	   	     </ul>
    	   	 </div>
    	   	 <div class="tea_tables">
    	       <table>
			    <tbody class="tabod">
			       <tr 
			       	v-for="(itemgridData,index) in gridData"
			       	:key="index"
			       	>
			        <td 
			        v-for="(item,index) in itemgridData">
			        {{item}}
			        </td>
			      </tr>
			    </tbody>
			  </table>
			 </div>
			 <div class="block"style="padding:20px 0px;">
			    <el-pagination
			      @size-change="handleSizeChange"
			      @current-change="handleCurrentChange"
			      :current-page="currentPage4"
			      :page-sizes="[100, 200, 300, 400]"
			      :page-size="100"
			      layout="total, sizes, prev, pager, next, jumper"
			      :total="400">
			    </el-pagination>
			</div>
    	   </div>
	  </div>
	</div>
</template>

<script>
export default{
	name :'examine',
	props:{
      data_list:{
			type:Object
		}
	},
	data(){
		return{ 
		data:["序号","任教课程","任教教师","任教时间","任教院校","任教年级","任教班级","实训次数"],
		gridData: [
	      { id:'01',name: '基础会计', teacher: '张三',when:'2017-2018年第二学期1', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'02',name: '基础会计', teacher: '张三1',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'03',name: '基础会计', teacher: '张三2',when:'2017-2018年第二学期2', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'04',name: '基础会计2', teacher: '张三3',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'05',name: '基础会计2', teacher: '张三4',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计2', teacher: '张三5',when:'2017-2018年第二学期3', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计3', teacher: '张三6',when:'2017-2018年第二学期4', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计3', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计3', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计4', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计4', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计4', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计4', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
	      { id:'06',name: '基础会计5', teacher: '张三',when:'2017-2018年第二学期', college: '会计学院',classs:'2015级',tea_class:'1701、1702、1703',degree:'3'},
       ],
        currentPage1: 5,
        currentPage2: 5,
        currentPage3: 5,
        currentPage4: 4
     }
	},
	computed:{
		examine(){
			return this.$store.state
		}
	},
	mounted(){
      this.$store.commit("secondrouterCtrl",false);
	},
    destroyed() {
      this.$store.commit("secondrouterCtrl",true)
    },
    methods:{
    handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
	    },
    handleCurrentChange(val) {
	        console.log(`当前页: ${val}`);
	    }
    }
}
</script>


<style scoped>
.mission{
     background-color: white;
     padding-top: 10px;
     margin-top: 5px;
}
.tea_t{
	margin-left: 25px;
}
.task_top{
	padding-left: 25px;
	margin-top: 25px;
	margin-bottom: 10px;
	border-bottom: 10px solid #f0f2f5;
}
.task_top>p{
	font-weight: 600;
}
.t_task_t{
	margin-bottom: 25px;
	display: flex;
}
.t_task_t>li{
	width:30%;
}
.t_task_t>li>b{
	display: inline-block;
	font-weight: 400;
	width:70px;
	height:22px; 
	font-size:14px;
	font-family:PingFangSC-Regular;
	color:rgba(0,0,0,0.85);
	line-height:22px
}
.t_task_t>li>span{
	display: inline-block;
	width:200px;
	height:22px; 
	font-size:14px;
	font-family:PingFangSC-Regular;
	color:rgba(0,0,0,0.65);
	line-height:22px;
	text-overflow: ellipsis;
	white-space: nowrap;
}
.tea_table{
   margin-top: 16px;
   font-size:12px;
   font-family:PingFangSC-Regular;
   color:rgba(104,113,120,1);
   margin-left: 25px;
   margin-right: 25px;
}
.tea_table thead{
    height: 48px;
}
.tea_table_top ul{
	display: flex;
	height:48px; 
	background:rgba(248,248,248,1);
	box-shadow: 0px -1px 0px 0px rgba(232,232,232,1);
	border-radius: 2px 2px 0px 0px ; 
	margin-bottom: 0px;
}
ul{
	-webkit-padding-start: 0px;
}
.tea_table_top ul>li{
	text-align: center;
	height: 48px;
	line-height: 48px;
	width: 100%;
}
.tea_tables{
	height: 500px;
	overflow-y: scroll;
}
.tabod>tr>td{
	text-align: center;
    width: 1%;
}
.tabod>tr{
	height: 48px;
	line-height: 48px;
	cursor: pointer;
}
.tabod>tr:hover{
	cursor: pointer;
	background-color: rgba(21,124,240,0.4);
	color: white;
}
table{ 
    border-collapse:collapse;
    width: 100%;    
}
.tea_table_top ul{
	display: flex;
	height:48px; 
	background:rgba(248,248,248,1);
	box-shadow: 0px -1px 0px 0px rgba(232,232,232,1);
	border-radius: 2px 2px 0px 0px ; 
	margin-bottom: 0px;
}
ul{
	-webkit-padding-start: 0px;
}
.tea_table_top ul>li{
	text-align: center;
	height: 48px;
	line-height: 48px;
	width: 100%;
}
.tea_table_top ul>li:nth-child(1){
	width: 86%;
}
.tea_table_top ul>li:nth-child(2){
	width: 86%;
}
.tea_table_top ul>li:nth-child(5){
	width: 80%;
}
.tabod>tr>td:nth-child(5){
	padding-left: 1%;
}
</style>