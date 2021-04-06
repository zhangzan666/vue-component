<template>
  <div id="app">
    <tree-com :staffArr='staffArr'/>
  </div>
</template>

<script>
  import TreeCom from './components/TreeCom'
export default {
  name: 'App',
  data() {
    return {
      staffArr: [
        {name: '1',class: 1,children: [
          {name:'1-1', children: [
            {name:'1-1-1'},
            {name:'1-1-2'},
            {name:'1-1-3',children: [
              {name: '1-1-3-1'},
              {name: '1-1-3-2'},
            ]},
          ]},
          {name: '1-2', children: [
            {name:'1-2-1'},
            {name:'1-2-2'},
            {name:'1-2-3'},
            {name:'1-2-4'},
          ]},
          {name: '1-3',children: [
            {name: '1-3-1'},
            {name: '1-3-2'},
            {name: '1-3-3',children: [
              {name: '1-3-3-1'},
            ]}
          ]},
        ]}
      ]
    }
  },
  components: {
    TreeCom
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
