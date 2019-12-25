<template>
  <div class="home">
  </div>
</template>

<script>
/*
    axios请求方法：get,post,put,patch,delete
    get方法：获取数据
    post方法：提交数据  （表单提交，文件上传）  一般用于新建
    put方法：更新数据  （所有数据推送到后端）   一般用于编辑
    patch方法： 更新数据  （只将修改的数据推送到后端）  一般用于编辑
    delete方法：删除数据
*/

import axios from 'axios'
export default {
  name: 'axios2-2',
  components: {

  },
  created(){
      //get请求
      // http://localhost:8081/data.json?id=12
      axios.get('/data.json',{
          params:{
              id:12
          }
      }).then((res)=>{
          console.log(res);
      })

      axios({
          method:'get',
          url:'/data.json',
          params:{
              id:12
          }
      }).then(res=>{
          console.log(res);
      })

      //post请求
      //form-data  表单提交  (图片上传，文件上传)
      //application/json
      let data = {
          id:12
      }
      axios.post('/post',data).then(res => {
          console.log(res);
      })

      axios({
          method:'post',
          url:'/post',
          data:data
      }).then(res => {
          console.log(res);
      })

      //form-data请求
      let formData = new FormData();
      for(let key in data){
          formData.append(key,data[key])
      }
      axios.post('/post',formData).then(res => {
          console.log(res);
      })

      //put请求
      axios.put('/put',data).then(res => {
          console.log(res);
      })

      //patch请求
      axios.patch('/patch',data).then(res => {
          console.log(res);
      })

      //delete请求
      axios.delete('/delete',{
          params:{
              id:12
          }
      }).then(res => {
          console.log(res);
      })

      axios.delete('/delete',{
          data:{
              id:12
          }
      }).then(res => {
          console.log(res);
      })

      axios({
          method:'delete',
          url:'/delete',
          params:{},
          data:{
              id:12
          }
      }).then(res => {
          console.log(res);
      })
  }
}
</script>
