<template>
  <doc :name="name"
    :desc="desc"
    :parms="parms"
    :code="code"
    >
    <we-search-bar :search="search" :focus="focus" :cancel="cancel"></we-search-bar>
  </doc>
</template>

<script>
  import 'weui/dist/style/weui.css'
  import Doc from 'bz-doc'
  import WeSearchBar from './Bz'
  export default {
    components: {
      Doc,
      WeSearchBar
    },
    data: function () {
      return {
        name: 'bz-weui-search-bar',
        desc: 'weui 的 searchbar 封装, 需要 weui.css',
        parms: [
          {parm: 'search', desc: '按下查找的回调函数'},
          {parm: 'focus', desc: '焦点时候的回调函数(可以不传入)'},
          {parm: 'cancel', desc: '点取消时的时候的回调函数(可以不传入)'}
        ],
        code: `<we-search-bar :search="search" :focus="focus" :cancel="cancel"></we-search-bar>`
      }
    },
    methods: {
      search: function (search_key) {
        window.alert('查找' + search_key)
      },
      focus: function () {
        console.log('focus时候，干些什么')
      },
      cancel: function () {
        console.log('cancel时候，干些什么')
      }

    }
  }
</script>
<style>
</style>
