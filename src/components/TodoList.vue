<script setup>
import { ref } from "vue";

const tasks = ref([
    { name: "線形代数課題", done: false },
    { name: "物理学実験レポート",done: false },
])

const newTaskName = ref("");
const addTask = () => {
    tasks.value.push({ name: newTaskName.value, done: false });
};
</script>

<template>
    <div>
        <div>TodoList</div>
        <div v-for="task in tasks" :key="task.name">
            <div v-if="task.done == false">
                <div class="task">
                    <div class="name">
                        未完: {{ task.name }}
                            <button @click="task.done = true">完了</button>
                    </div>
                </div>
            </div>
        </div>
        <div>
            <div>Completed Tasks</div>
            <div v-for="task in tasks" :key="task.name">
                <div v-if="task.done == true">
                    <div class="task">
                        <div class="name">
                            完了: {{ task.name }}
                        </div>
                    </div>
                </div>
            </div>
            <label>
                タスクを入力: 
                <input v-model="newTaskName" type="text" />
            </label>
            <button @click="addTask">add</button>
        </div>
    </div>
</template>

<style></style>