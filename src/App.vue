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
import { ref } from 'vue'
import { useStore } from 'vuex'

export default {
  name: 'App',
  components:{
    Spinner,
    Form,
    Items,
    Empty
  },
  setup(){
    const loading = ref(false)
    const store = useStore()
    
    loading.value = true
    store.dispatch('getTodos').finally(() =>{
      loading.value = false
    })

    return {
      loading,
    }
  }
}
</script>