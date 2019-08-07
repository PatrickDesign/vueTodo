<template>
    <div>
        <div :key="todo.id" v-for="todo in todos">
            <TodoItem :todo="todo" :del="del" @del-todo="$emit('del-todo', todo.id)"/>
        </div>
    </div>
</template>

<script>

import TodoItem from './TodoItem';

export default {
    name: "Todos",
    props: ["todos"],
    components: {
        TodoItem
    },
    methods: {
        del(id){
            this.todos = this.todos.filter(todo => todo.id != id)
        }
    }
}
</script>


<style>

</style>


