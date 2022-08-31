<!--
 * @Author: hjhj111 2268716068@qq.com
 * @Date: 2022-08-30 12:15:37
 * @LastEditors: hjhj111 2268716068@qq.com
 * @LastEditTime: 2022-08-31 10:55:45
 * @FilePath: \note_book\src\components\HelloWorld.vue
 * @Description: 这是一个简单基于vue的在线备忘录,结合c++网络库Rester，内存数据库redis使用
-->
<template>
  <div>
    <h1>数据服务器地址: {{ address }}</h1>
    <ol style="list-style-type:none">
      <li v-for="note in notes" :key="note.text">
        <h2>{{note.text}}</h2>
        <button @click="deleteNote(note)">完成待办</button>
      </li>
    </ol>
    <!-- <form action={{this.adress}} method="post"> -->
      <input type="text"  id="form" placeholder="添加待办……">
      <input type="submit" value="确认添加" @click="addNote">
    <!-- </form> -->
  </div>  
</template>

<script>
//import { setgroups } from 'process';
import axios from 'axios'

export default {
  name: 'NoteBook',

  data(){
    return{
      notes:[
        {text:"hhhh"},
        {text:"jjjjj"}
      ],
      Address: this.address
    }    
  },

  props: {
    address:{default: "no url for data"},    
  },

  created(){
    this.getNotes()
    console.log(this.notes)  
  },
  
  methods:{   

    getNotes: function(){       
    console.log(this.address)        
    var self=this//修改父对象，函数也是对象
    axios.get(this.address).then(function(res){    
    console.log(res.data)
    self.notes=res.data
    console.log(self.notes)  
    }    
    ).catch((err)=>{
      console.log(err)      
    })    
    },

    addNote: function(){
      var self=this
      console.log(document.getElementById("form").value)
      axios({
        method:"Post",
        url:self.address,
        headers:{
          'Content-Type': 'text/plain'//application/json
        },
        data:{text:document.getElementById("form").value}
        //data:"{\"text\":\"更加发奋建安费\"}"
      }).then(function(res){
        if(res.status==201){
          //update
          self.getNotes();
          alert("添加完成");
        }
        else{
          alert("添加失败");
        }
      })
      
    },
    
    deleteNote: function(note){
      var self=this
      axios({
        method:"Delete",
        url:self.address,
        data:note
      }).then(function(res){
        if(res.status==201){
          //update
          self.getNotes()
          alert("删除成功")
        }
        else{
          alert("删除失败")
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
