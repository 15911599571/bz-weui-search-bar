<template>
  <div  v-bind:class="{ 'weui_search_focusing': is_focus || search_key}" class="weui_search_bar">
    <form v-on:submit.prevent="call" class="weui-search-bar__form">
      <div class="weui-search-bar__box">
        <i class="weui-icon-search"></i>
        <input v-model="search_key" @focus="focus" @blur="blur" type="search" class="weui-search-bar__input" id="search_input" placeholder="搜索" required/>
        <a href="javascript:" class="weui-icon-clear"></a>
      </div>
      <label v-show="!is_focus && !search_key" for="search_input" class="weui-search-bar__label">
        <i class="weui-icon-search"></i>
        <span>搜索</span>
      </label>
    </form>
    <a v-show="is_focus || search_key" @click="clean" href="javascript:" class="weui-search-bar__cancel-btn">取消</a>
  </div>
</template>

<script>
  export default {
    props: {
      search: {
        required: true
      },
      cancel: {
      }
    },
    components: {
    },
    data: function () {
      return {
        search_key: null,
        is_focus: false
      }
    },
    ready () {
    },
    methods: {
      focus: function () {
        this.is_focus = true
        if (this.focus_run) {
          this.focus_run()
        }
      },
      blur: function () {
        this.is_focus = false
      },
      clean: function () {
        this.search_key = null
        if (this.cancel) {
          this.cancel()
        }
      },
      call: function () {
        this.search(this.search_key)
      }

    }
  }
</script>
