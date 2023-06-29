<template>
    <a-card :title="item.title" :bordered="false"  id="card">
        <p>{{ item.description }}</p>
        <a-button type="primary" @click="editItem(item.id)">
            <template #icon>
                <EditOutlined />
            </template>
            Edit
        </a-button>
        <a-button type="danger" @click="deleteItem(item.id)">
            <template #icon>
                <DeleteOutlined />
            </template>
            Delete
        </a-button>
    </a-card>
</template>

<script>
import {EditOutlined, DeleteOutlined} from '@ant-design/icons-vue';
export default {
    name: "TodoItem",
    props: ['item'],
    components:{
        EditOutlined, DeleteOutlined
    },
    methods: {
        editItem(id) {
            this.$emit("editItem", {id})
        },
        deleteItem(id) {
            this.$emit("deleteItem", {id})
        },
    }
}
</script>


<style scoped>
#card {
    margin-top: 10px;
}
</style>