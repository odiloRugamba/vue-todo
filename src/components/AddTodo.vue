<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add task">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>
<script>
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
}
</script>
<style scoped>
form{
    display: flex;
}
input[type="text"] {
    flex: 10;
    padding: 5px;
    padding: 20px;
    border: none;
    border-top: 1px solid #000000;
}
input[type="Submit"] {
    flex: 2;
    padding: 20px;
    
}
</style>