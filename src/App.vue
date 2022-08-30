<!--
 * @Author: hjhj111 2268716068@qq.com
 * @Date: 2022-08-30 12:15:37
 * @LastEditors: hjhj111 2268716068@qq.com
 * @LastEditTime: 2022-08-30 17:11:38
 * @FilePath: \note_book\src\App.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <img alt="Vue logo" src="./assets/main.jpg">
  <NoteBook address="http://192.168.56.101:5000/notes"/>
</template>

<script>
import NoteBook from './components/NoteBook.vue'


export default {
  name: 'App',
  components: {
    NoteBook
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
