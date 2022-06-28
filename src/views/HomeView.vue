<template>
  <div id="app">
    <div class='qualityManual-container'>
      <div>
        <button style='width: 120px;' type='primary' @click='getFile'>测试预览office文档</button>
        <button style='width: 120px;' type='primary' @click='close'>关闭</button>
      </div>
      <div v-if='show' class='qualityManual-container-office'>
        <vab-only-office :option='option' />
      </div>
    </div>
  </div>
</template>

<script>
  import vabOnlyOffice from '@/components/VabOnlyOffice'

  export default {
    name: 'App',
    components: {
      vabOnlyOffice
    },
    data() {
      return {
        //参考vabOnlyOffice组件参数配置
        option: {
          url: '',
          isEdit: '',
          fileType: '',
          title: '',
          lang: '',
          isPrint: '',
          user: {
            id: null,
            name: ''
          }
        },
        show: false,
      }
    },
    methods: {
      getFile() {

        // getAction('/file/selectById', { id: this.id }).then(res => {
        this.option.isEdit = true
        this.option.lang = 'zh-CN'
        // this.option.url = 'http://video.zkblog.ltd/%E6%96%B0%E5%BB%BA%20XLS%20%E5%B7%A5%E4%BD%9C%E8%A1%A8%20(2).xls'
        this.option.url = 'http://video.zkblog.ltd/%E9%9D%A2%E8%AF%95%E9%A2%98.doc'
        this.option.title = '123'
        this.option.fileType = 'doc'
        this.option.isPrint = true
        this.option.user = {
          id: 12,
          name: '李四'
        }
        this.show = true
        // })
      },
      close() {
        this.show = false
      },
    },
  }
</script>

<style>
  .qualityManual-container {
    padding: 0 !important;
    height: 100%;
  }

  .qualityManual-container-office {
    width: 100%;
    height: calc(100% - 55px);
  }
</style>
