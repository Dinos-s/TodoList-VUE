<template>
  <div class="px-3 py-10 md:px-10">
    <div class="w-full sm:w-1/2 lg:w-1/3 mx-auto">
      <Spinner v-if="loading"/>
      <template v-else>
        <Form/>
        <Items v-if="$store.state.todos.length"/>
        <Empty v-else/>
      </template>
     </div>
  </div>
</template>

<script>
import Spinner from './components/todoSpinner.vue'
import Form from './components/todoForm.vue'
import Items from './components/todoItems.vue'
import Empty from './components/todoEmpty.vue'
export default {
  name: 'App',
  data() {
    return{
      loading: false,
    }
  },
  components:{
    Spinner,
    Form,
    Items,
    Empty
  },
  created(){
    this.loading = true
    this.$store.dispatch('getTodos').finally(()=>{
      this.loading = false
    })
  }
}
</script>