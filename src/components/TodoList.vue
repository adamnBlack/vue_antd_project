<template>
    <add-item @newItem="newItem" @updateItem="updateItem" :mtype="modalType" :data="item"/>
    <div style="background-color: #ececec; padding: 20px">
      <a-row :gutter="16">
        <a-col :span="8" v-for="item in itemList" :key="item.id">
            <todo-item :item="item" 
            @editItem="handleEdit" @deleteItem="handleDelete"/>
        </a-col>
      </a-row>
    </div>
  </template>

<script>
import TodoItem from "./TodoItem.vue";
import AddItem from "./AddItem.vue";

export default {
    name: "TodoList",
    components: {TodoItem, AddItem},
    data(){
        return  {
            modalType: false,
            item: {},
            itemList: [
                {id:0, title: "FirstDay", description: "Today is firstday"},
                {id:1, title: "SecondDay", description: "Today is secondday"},
                {id:2, title: "Thirdday", description: "Today is thirdday"},
            ]
        }
    },
    methods: {
        handleEdit({id}){
            console.log("modalTye", this.modalType);
            this.item = this.itemList.filter(item => item.id === id)[0];
            this.modalType = true;
            console.log("data", this.item);
        },
        handleDelete({id}){
            var {itemList} = this;
            itemList = itemList.filter(item => item.id !== id);
            this.itemList = [...itemList];
        },
        newItem({title, description}){
            console.log("newData", title)
            this.modalType = false;
            var {length} = this.itemList;
            var newData = {
                id: this.itemList[length - 1].id + 1,
                title, description
            }
            this.itemList.push(newData);
        },
        updateItem({id, title, description}){
            this.modalType = false;
            var {itemList} = this;
            itemList = itemList.map(item => {
                if (item.id === id){
                    item.title = title;
                    item.description = description;
                }
            })
            console.log("updateItem, itemList", itemList);
            this.itemList = [...itemList];
        }
    }
}
</script>