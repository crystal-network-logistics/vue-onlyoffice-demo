<template>
    <div>
      <div v-for="item,index in list" :key="index">
        {{item.name}}
        <mu-button @click="handleClick(item.id)" flat color="primary">编辑</mu-button>
      </div>
    </div>
</template>

<script>


  export default {
    name: 'App',
    data() {
      return {
        list:[
          {name:'我的文档1.doc',id:1},
          {name:'我的文档2.xls',id:2},
          {name:'我的文档3.xls',id:3},
          {name:'我的文档4.doc',id:4},
          {name:'我的文档5.txt',id:5},
        ]
      }
    },
    methods:{
      handleClick(val){
        this.$router.push({
            path: '/detail', 
            query: { id: val }
        })
      }
    }
  }
</script>
