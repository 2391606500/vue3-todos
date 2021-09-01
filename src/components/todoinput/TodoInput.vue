<template>
  <form class="form-inline" @submit.prevent="addlist">
    <div class="input-group mb-2 mr-sm-2">
      <div class="input-group-prepend">
        <div class="input-group-text">任务</div>
      </div>
      <input type="text" class="form-control" placeholder="请输入任务信息" style="width: 356px" v-model.trim="task"/>
    </div>

    <button type="submit" class="btn btn-primary mb-2">添加新任务</button>
  </form>
</template>

<script>
export default {
name:"TodoInput",
data(){
  return{
    task:''
  }
},
emits:['addList'],

methods:{
  addlist(){
    if(!this.task)return alert('任务列表不能为空')
    this.$emit('addList',this.task)
    this.task=""
  }
}
}
</script>

<style lang="less" scoped>

</style>