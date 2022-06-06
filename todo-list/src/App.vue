<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <MyHeader @addTodo="addTodo"/>
    <MyList :todos="todos"/>
    <MyFooter :todos="todos" :checkAll="checkAll" :deleteDone="deleteDone"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader'
import MyList from './components/MyList'
import MyFooter from './components/MyFooter'

export default {
  name: 'App',
  data() {
        return {
        todos:JSON.parse(localStorage.getItem('todos')) || []
        }        
    },
  components: {
    MyHeader,MyList,MyFooter
  },
  mounted() {
    this.$bus.$on('checkTodo',(id)=>{    
        this.todos.forEach(element => {
        if(element.id === id) element.checked=!element.checked
      })})
      this.$bus.$on('deleteTodo',this.deleteTodo)
  },
  methods: {
    addTodo(todoObj) {
      this.todos.unshift(todoObj)
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    checkAll(checked) {
      this.todos.forEach(todo => todo.checked = checked)
    },
    deleteDone() {
      this.todos=this.todos.filter(todo => todo.checked!==true)
    }
  },
  watch: {
    todos: {
      deep: true,
      handler(value) {
        localStorage.setItem('todos',JSON.stringify(value))
      }
    }
  },
  beforeDestroy() {
    this.$bus.$off(['checkTodo','deleteTodo'])
  },
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
