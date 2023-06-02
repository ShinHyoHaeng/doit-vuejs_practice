<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo"><i class="addBtn fa fa-plus" area-hidden="true"></i></span>
        <!-- <button @click="addTodo">추가</button> -->

        <!-- <modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3>
            <span slot="footer" @click="showModal = false">
                <i class="closeModalBtn fa fa-times" area-hidden="true"></i>
            </span>
        </modal> -->
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo() {
            if (this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
    input:focus{outline:none;}
    .inputBox{background: white; height: 50px; line-height: 50px; border-radius: 5px;}
    .inputBox input{border-style: none; font-size: 0.9rem;}
    .addContainer{float:right; background: linear-gradient(to right, #6478fb, #8763fb); display:inline-block; width: 3rem; border-radius: 0 5px 5px 0;}
    .addBtn{color:white; vertical-align: middle;}
</style>
