<template>
    <div>
        <input type="text" v-model="todoText" placeholder="Введите задачу">

        <button @click="add" :disabled="!todoText">Добавить</button>
        <button @click="deleteAll">Удалить все</button>

        <div v-for="(task, key) in tasks" :key="key">
            <span>{{ key + 1 }}. {{ task.text }}</span>
            <button @click="deleteElement(key)">Удалить</button>
        </div>

    </div>
</template>


<script>
    export default {
        name: "Todo",
        data() {
            return {
                todoText: '',
                tasks: [],
            }
        },
        methods: {
            add() {
                this.tasks.push({ text: this.todoText});
                this.todoText = '';
            },
            deleteAll() {
                this.tasks = [];
            },
            deleteElement(key) {
                this.tasks.splice(key, 1);
            },
        }
    }
</script>


<style scoped>

</style>