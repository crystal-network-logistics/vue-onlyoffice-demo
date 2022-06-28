<template>
    <div class='qualityManual-container'>
        <div v-if='show' class='qualityManual-container-office'>
            <vab-only-office :option='option' />
        </div>
    </div>
</template>
<script>
import vabOnlyOffice from '@/components/VabOnlyOffice'
export default {
    components: {
        vabOnlyOffice
    },
    data() {
        return {
            //参考vabOnlyOffice组件参数配置
            option: {
                url: '',
                isEdit: true,
                fileType: '',
                title: '',
                lang: 'zh-CN',
                isPrint: true,
                user: {
                    id: 1,
                    name: '张三'
                }
            },
            show: false,
            list:[
                {name:'我的文档1.doc',id:1,title:'我的文档1.doc',url:'http://video.zkblog.ltd/%E9%9D%A2%E8%AF%95%E9%A2%98.doc',fileType:'doc'},
                {name:'我的文档2.xls',id:2,title:'我的文档2.xls',url:'http://video.zkblog.ltd/%E6%96%B0%E5%BB%BA%20XLS%20%E5%B7%A5%E4%BD%9C%E8%A1%A8%20%282%29.xls',fileType:'xls'},
                {name:'我的文档3.xls',id:3,title:'我的文档3.xls',url:'http://video.zkblog.ltd/%E6%96%B0%E5%BB%BA%20XLS%20%E5%B7%A5%E4%BD%9C%E8%A1%A8%20%282%29.xls',fileType:'xls'},
                {name:'我的文档4.doc',id:4,title:'我的文档4.doc',url:'http://video.zkblog.ltd/%E9%9D%A2%E8%AF%95%E9%A2%98.doc',fileType:'doc'},
                {name:'我的文档5.txt',id:5,title:'我的文档5.txt',url:'http://video.zkblog.ltd/idea%E6%BF%80%E6%B4%BB%E7%A0%81.txt',fileType:'txt'},
            ]
        }
    },
    created(){
        this.loadOnlyOffice(this.$route.query.id)
    },
    methods:{
        loadOnlyOffice(val){
            let optionTemp = {}
            for(let i=0;i<this.list.length;i++){
                if(this.list[i].id == val){
                    optionTemp = this.list[i]
                    break;
                }
            }
            this.option.name = optionTemp.name
            this.option.id = optionTemp.id
            this.option.title = optionTemp.title
            this.option.url = optionTemp.url
            this.option.fileType = optionTemp.fileType
            console.log(this.option)
            this.show = true
        }
    }
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