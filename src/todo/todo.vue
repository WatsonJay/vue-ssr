<template>
    <section class="real-app">
        <input
           type="text"
           class="add-input"
           autofocus="autofocus"
           placeholder="计划做什么事"
           @keyup.enter="addTodo"
        >
        <Item
                :todo="todo"
                v-for="todo in todos"
                :key="todo.id"
                @del="deleteTodo"
        />
        <Tabs :filter="filter"></Tabs>
    </section>
</template>

<script>
    import Item from './item.vue'
    import Tabs from './tabs.vue'
    let id=0
    export default {
        name: "todo",
        data(){
          return{
              todos:[],
              filter: 'all'
          }
        },
        components:{
            Item,
            Tabs,
        },
        methods:{
            addTodo(e) {
                this.todos.unshift({
                    id: id++,
                    content: e.target.value.trim(),
                    completed: false
                })
                e.target.value = ''
            },
            deleteTodo(id){
                this.todos.splice(this.todos.findIndex(todo => todo.id === id ), 1)
            }
        }
    }
</script>

<style lang="stylus" scoped>
.real-app {
    width 600px
    margin 0 auto
    box-shadow 0 0 5px #666
}
.add-input{
    position: relative;
    width: 100%;
    font-size: 20px;
    font-family: inherit;
    font-weight: inherit;
    line-height: 1.4em;
    border: 0;
    outline none;
    color: inherit;
    padding: 6px;
    box-shadow: inset 0 -1px 5px 0 rgba(0,0,0,0.5);
    box-sizing: border-box;
    font-smoothing: antialiased;
    padding: 16px 16px 16px 60px;
    border: none;
    box-shadow: insert 0 -2px 1px rgba(0,0,0,0.5);
}
</style>