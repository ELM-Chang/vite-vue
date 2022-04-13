<template>
{{event.title}}
<base_input v-model="event.title" label="Title" type="text"/>
<p>{{text}}</p>
<input type="text" v-model="text">
<button type="button" @click="addItem">新增文字</button> 
<ul>
    <li v-for="item in data" :key="item.id">
        {{item.text}}
        <button type="button" @click="editItem(item)">添加項目</button>
        <button type="button" @click="removeItem(item)">移除項目</button>
    </li>
</ul>
<input type="text" v-model="temp.text">
<button type="button" @click="doneItem(item)">編輯文字</button> 
  <!-- <base_input v-model="event.title" 
  label="Title" type="text"/> -->
</template>
<script>
import base_input from './base_input.vue'
export default{
data() {
    return {
        text: '',
        data: [],
        temp: {},
        event:{
            title: "from todo_list"
        }
    }
},
methods: {
    addItem(){
        this.data.push({
            id: this.data.length+1,
            text: this.text
        });
        this.text='';
    },
    removeItem(item){
        // findIndex
        const index = this.data.findIndex(obj => obj.id ===
        item.id);
        this.data.splice(index,1);
        // splice(index,count)
        console.log(index,item.id);
    },
    editItem(item){
        this.temp = {...item}
    },
    doneItem(){
        const index = this.data.findIndex(obj => obj.id ===
        this.temp.id);
        this.data[index]=this.temp;
        this.temp={};
    }
},
components:{
    'base_input':base_input
}
}

</script>
