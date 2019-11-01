<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
  </div>
</template>
<script>
import { APPKEY } from './core/var'
export default {
  created () {
    let time = new Date().getTime()
    const signature = md5(`appkey=${APPKEY}&timestamp=${time}&random_str=022cd9fd995849b58b3ef0e943421ed9&key=5a4420a03fae3ed6f8f5b658`)
    JIM.init({
      'appkey': '4b2282f104fd980412936c5f',
      'random_str': '022cd9fd995849b58b3ef0e943421ed9',
      'signature': signature,
      'timestamp': time,
      flag: 0
    }).onSuccess(function (data) {
      JIM.register({
        'username': '112222',
        'password': '123456',
        'is_md5': true,
        'extras': { 'key1': 'val1', 'key2': 'val2' },
        'address': '深圳'
      }).onSuccess(function (data) {
        console.log(data)
        // data.code 返回码
        // data.message 描述
      }).onFail(function (data) {
        console.log(data, 'error')
        // 同上
      })
      // data.code 返回码
      // data.message 描述
    }).onFail(function (data) {
      // 同上
    })
  }
}
</script>
<style lang="less">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
