<template>
    <div>
      <a-button type="primary" @click="showModal">Add</a-button>
      <a-modal v-model:visible="visible" title="Basic Modal" @ok="handleOk">
        <label>Title</label><a-input type="text" v-model:value="title"/>
        <label>Description</label><a-textarea rows="10" v-model:value="description"/>
      </a-modal>
    </div>
  </template>
  <script>
  export default {
    name: "AddItem",
    props: ['mtype', 'data'],
    data(){
        return {
            title: '',
            description: '',
            visible: false,
        }
    },
    methods:{
        showModal(){
            this.visible = true;
        },
        handleOk(e){
            if (this.mtype){
                this.$emit("updateItem", {id: this.data.id, title: this.title, description: this.description});
            }
            else{
                this.$emit("newItem", {title: this.title, description: this.description});
            }
            
            this.title = '';
            this.description = '';
            this.visible = false;
      },
    }
  };
  </script>
