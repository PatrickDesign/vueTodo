<template>
    <div class="todo-item" :class="{'is-complete' : todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}</p>
            <button class="del" @click="$emit('del-todo', todo.id)">X</button>

        <!-- <p>Todo Item</p>
        <ul>
            <li>title: {{todo.title}}</li>
            <li>id: {{todo.id}}</li>
            <li>Completed? {{todo.completed ? "Yes!!" : "nope.... XD"}}</li>
        </ul> -->
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete(event)
        {
            this.todo.completed = event.target.checked
        }
    }
}
</script>

<style>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete {
        text-decoration: line-through;
    }
    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>


