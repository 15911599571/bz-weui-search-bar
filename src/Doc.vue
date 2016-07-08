<template>
  <div class="ui container segment">
    <h1>{{name}}</h1>
    <p>{{desc}}</p>
    <table class="ui celled table">
      <thead>
        <tr><th>参数</th><th>说明</th></tr>
      </thead>
      <tbody>
        <tr v-show="parm_desc">
          <td colspan="2" v-html="parm_desc"></td>
        </tr>
        <tr v-for="parm in parms"> <td class="single line"> {{parm.parm}} </td> <td> {{parm.desc}} </td></tr>
        <tr v-show="parms.length===0">
          <td colspan="2"></td>
        </tr>
      </tbody>
    </table>
    <code v-text="code"></code>
    <div class="ui divider"></div>
    <button v-show="run" @click='run' class='ui basic button'>
      <i class='icon play'></i>
      运行
    </button>
    <we-search-bar :search="search" :focus="focus" :cancel="cancel"></we-search-bar>
  </div>
</template>

<script>
  import 'semantic-ui/dist/components/site.css'
  import 'semantic-ui/dist/components/reset.css'
  import 'semantic-ui/dist/components/table.css'
  import 'semantic-ui/dist/components/container.css'
  import 'semantic-ui/dist/components/divider.css'

  import 'weui/dist/style/weui.css'
  import WeSearchBar from './Bz'
  export default {
    components: {
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
<style lang=less>
  .original-text-bz {
    /*保留空格*/
    white-space: pre-wrap;
    /*字体能自动换行*/
    word-wrap:break-word;
  }
  code {
    padding: 2px 4px;
    font-size: 90%;
    color: #c7254e;
    background-color: #f9f2f4;
    border-radius: 4px;
    .original-text-bz;
  }
</style>
