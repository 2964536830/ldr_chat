<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text href="https://github.com/vuetifyjs/vuetify/releases/latest" target="_blank">
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-app-bar>

    <v-content>
      <HelloWorld />
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import { APPKEY } from './core/var'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: () => ({
    //
  }),
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
