<template>
  <div>
    <label for="task">Tarefas</label><br />
    <input v-model="task" type="text" id="task" />
  </div>
  <div>
    <label for="time">Tempo gasto</label><br />
    <input v-model="time" type="number" id="time" />
  </div>
  <button @click="addTaskTime">Adicionar</button>
  <div><p>Lista de tarefas</p></div>
  <div v-for="(item, index) of list" :key="index">
    <TaskListVue :task="item.task" :time="item.time" :index="index" @changeTime="calcTotalTime" />
  </div>
  <div>
    <label for="timeUsed">Total de tempo gasto: {{ totalTime }}</label>
  </div>
</template>

<script setup>
import { ref, computed, reactive } from 'vue'
import TaskListVue from './TaskList.vue'

const task = ref('')
const time = ref(0)
const list = reactive([])
const totalTime = ref(0)

function addTaskTime() {
  console.log(task.value, time.value)
  list.push({ task: task.value, time: time.value })
  totalTime.value += time.value
}
function calcTotalTime(timeTask) {
  totalTime.value -= timeTask
}
</script>

<style></style>
