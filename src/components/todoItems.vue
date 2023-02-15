<template>
    <div class="space-y-2">
        <Item v-for="todo in $store.state.todos" :key="todo.id" :todo="todo"/>
    </div>
</template>

<script>
import Item from "@/components/todoItem";
export default {
    name: 'todoItems',
    components:{
        Item
    }
}
</script>