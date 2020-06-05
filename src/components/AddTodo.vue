<template>
    <div>
        <form>
            <input type="text" name="title" id="" placeholder="Add Todo..." v-model="title">
            <input type="submit" value="Submit" class="btn" @click="addTodo">
        </form>
    </div>
</template>

<script>
    import {v4} from 'uuid';
    export default {
        name: "AddTodo",
        data(){
            return{
                title:''
            }
        },
        methods:{
            addTodo(e){
                e.preventDefault();
                if(!this.title.trim()) return;
                const newTodo = {
                    id: v4(),
                    title: this.title,
                    completed:false,
                }
                this.$emit('add-todo',newTodo);
                this.title = ''
            }
        }
    }
</script>

<style scoped>
    form{
        display: flex;
    }
    input[type="text"]{
        flex: 10;
        padding: 5px;
    }
    input[type="submit"]{
        flex:2;
    }
</style>