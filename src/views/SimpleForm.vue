<template>
    <base_input v-model="event.title" label="Title"
    type="text"/>
    {{event.title}}
    <p>other insert</p>
    <todo_list/>
</template>
<script>
import todo_list from '../components/todo_list.vue'
import base_input from '../components/base_input.vue'
export default {
    data() {
        return{
            event:{
                title:'from simple_form'
            }
        }
    },
    components:{
        'todo_list'  : todo_list,
        'base_input' : base_input
    }
}
</script>
