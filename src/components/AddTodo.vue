<template>
    <div>
        <form @submit="addTodo">
            <input type="text" name="title" v-model="title" placeholder="Add Todo...">
            <input type="submit" class="btn">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    methods: {
        addTodo(event)
        {
            event.preventDefault();
            if(this.title != '')
            {
                this.$emit('add-todo', {
                    title : this.title,
                    completed: false
                });
                this.title = '';
            }
        }
    },
    data() 
    {
        return {
            title: ''
        }
    }
}
</script>

<style>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>


