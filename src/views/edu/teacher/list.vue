<template>
  <div class="app-container">
    讲师列表
  </div>
</template>
<script>
import teacher from '@/api/edu/teacher.js'
//1. 引入调用teacher.js文件
export default {
    //核心代码位置
    //data方式一
    // data:{
    // },

    //data方式二  使用这种
    //{1} 
    data(){  //定义变量和初始值
        return{
            list:null,//查询之后接口返回集合
            page:1,//当前页
            limit:10,//每页记录数
            total:0,//总记录数
            tearchQuery:{}//条件封装对象
        }
    },
    //{3}
    created(){ //页面渲染之前执行 一般调用method定义的方法
        //调用
        this.getList()
    },
    //{2}
    methods:{ //创建具体的方法 调用teacher.js定义的方法
        //讲师列表的方法
        getList() {
            teacher.getTeacherListPage(this.page,this.limit,this.tearchQuery)
                .then(response =>{
                    //response接口返回的数据
                    console.log(response)
                })//请求成功
                .catch( error =>{
                    // console.log(error)
                })//请求失败
        }
    }
}
</script>