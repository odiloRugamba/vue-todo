<template>
    <div>
        <div v-bind:key="to.id" v-for="to in todos">
            <TodoItem v-bind:item="to" v-on:del-todo="$emit('del-tod', to.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './todoitem'
export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"],
}
</script>

<style scoped>

</style>