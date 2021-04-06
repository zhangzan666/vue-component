<template>
  <div class="tree_wrap">
    <div :class="{bottom_line: staffArr[0].class !== 1}"></div>
    <div v-for="(item, index) in staffArr" :key='index' class="item_box">
      <div :class="{ctrl:true,fifty:item.class !== 1 && staffArr.length> 1 && (index === 0 || index === staffArr.length - 1),hundred:item.class !== 1 && staffArr.length > 2 && (index !== 0 && index < staffArr.length - 1),turn_right: index === 0}"></div>
      <div class="item">
        <div :class="{top_line: item.class !== 1}"></div>
        <div class="name" @click="handleName(index)" ref="name_node">{{item.name}}</div>
        <!-- <div :class="{bottom_line:item.children}"></div> -->
      </div>
      <template v-if="item.children && item.children.length > 0" class="item_wrap">
        <TreeCom :staffArr='item.children'/>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TreeCom',
  props: {
    staffArr: {
      type: Array
    }
  },
  data() {
    return {
      showChildren: true
    }
  },
  methods: {
    handleName(index) {
      let children = this.$refs.name_node[index].parentNode.nextElementSibling
      if (children === null) return
      if (children.style.opacity !== '0') {
        console.log(1)
        children.style.opacity = 0
      }else {
        children.style.opacity = 100
      }
    }
  }
}
</script>

<style scoped>
.tree_wrap {
  display: flex;
}
.item_box {
  position: relative;
}
.item_box .ctrl{
  position: absolute;
  border-top: 4px solid #000;
}
.item_box .ctrl.fifty {
  width: 50%;
}
.item_box .ctrl.hundred {
  width: 100%;
}
.item_box .ctrl.turn_right {
  top: 0;
  right: 0;
}
.tree_wrap {
  position: relative;
}
.tree_wrap .item{
  margin: 0 10px;
  display: flex;
  justify-content: center;
  position: relative;
}
.tree_wrap .bottom_line {
  border-top: 20px solid #000;
  width: 4px;
  position: absolute;
  left: 50%;
  top: 0%;
  transform:  translateX(-2px) translateY(-20px);
}
.tree_wrap .item .name {
  border: 1px solid #000;
  white-space: nowrap;
  padding:5px 0px;
  width:60px;
  margin: 20px 0;
  cursor: pointer;
}
/* .tree_wrap .item .bottom_line {
  border-top: 20px solid #000;
  width: 4px;
  position: absolute;
  left: 50%;
  top: 100%;
  transform: translateY(-20px) translateX(-2px);
} */
.tree_wrap .item .top_line {
  border-top: 20px solid #000;
  width: 4px;
  position: absolute;
  left: 50%;
  top: 0%;
  transform: translateX(-2px);
}
</style>