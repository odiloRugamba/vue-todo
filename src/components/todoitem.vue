<template>
    <div class="todo-item" v-bind:class="{'is_completed': item.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete"> 
            {{item.title}}
            <button @click="$emit('del-todo', item.id)" class="del"> X </button>
        </p>
    </div>
</template>
<script>
export default {
    name: "TodoItem",
    props: ["item"],
    methods: {
        markComplete() {
            this.item.completed = !this.item.completed; 
        }
    }
}
</script>
<style scoped>
    .todo-item{
        background: #ffffff;
        border: 1px solid #cccccc;
        padding: 10px;

    }
    .is_completed{
        text-decoration: line-through;
    }
    .del{
        float: right;
        color: #ffffff;
        background: red;
        border: none;
        padding: 5px;
    }
</style>