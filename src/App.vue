<template>
<div>
<h1>111</h1>
</div>
<TodoInput @addList="addTodoList"></TodoInput>
<TodoList :list="tasklist"></TodoList>
<TodoButton v-model:active="activeIndex"></TodoButton>
</template>

<script>

import TodoList from './components/todolist/TodoList.vue'
import TodoInput from './components/todoinput/TodoInput.vue'
import TodoButton from './components/todobutton/TodoButton.vue'
export default {
  name: 'App',
  components: {
 TodoList,
 TodoInput,
 TodoButton
  },
  data(){
    return{
      todoList:[
        {id:1,task:"周一早晨9点开会",done:true},
        {id:2,task:"周二早晨9点开会",done:false},
        {id:3,task:"周三早晨9点开会",done:false}
      ],
      nextId:4,
      activeIndex:0
    }
  },
  methods:{
    addTodoList(task){
     this.todoList.push({
       id:this.nextId,
       task,
       done:false
     }),
     this.nextId++
    }
  },
  computed:{
  tasklist(){
  switch(this.activeIndex){
    case 0:
    return this.todoList
    case 1:
      return this.todoList.filter(x=>x.done===true)
    case 2:
      return this.todoList.filter(x=>x.done===false)
  }
  }
}
}
</script>
