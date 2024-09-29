<script setup lang="ts">
import { ref } from 'vue';
const name = ref('Ram');
const status = ref('active');
const tasks = ref([
  {
    id: 1,
    name: 'Task 1',
  },
  {
    id: 2,
    name: 'Task 2',
  }
]);
const taskName = ref('');

const handleStatusChange = () => {
  let updatedStatus;
  switch (status.value) {
    case "active":
      updatedStatus = "pending";
      break;
    case "pending":
      updatedStatus = "inactive";
      break;
    default:
      updatedStatus = "active";
  }
  status.value = updatedStatus
}

const handleSubmit = () => {
  if (taskName.value.trim() !== '') {
    tasks.value.push({
      id: tasks.value.length + 1,
      name: taskName.value,
    });

    taskName.value = "";
  }
}

const deleteTask = (index: number) => {
  tasks.value.splice(index, 1)
}

</script>

<template>
  <div>
    <h1>{{ name }}</h1>

    <p v-if="status === 'active'">User is active</p>
    <p v-else-if="status === 'pending'">User is pending</p>
    <p v-else>User is inactive</p>

    <form @submit.prevent="handleSubmit">
      <label for="task">Task Name</label>
      <input type="text" name="task" v-model="taskName" />

      <button type="submit">Submit</button>
    </form>

    <h3>Tasks</h3>
    <ul>
      <li v-for="(task, index) of tasks" :key="task?.id">
          <span>
            {{ task?.name }}
          </span>

          <button @click="deleteTask(index)">X</button>
      </li>
    </ul>

    <br />
    <button @click="handleStatusChange">Change Status</button>
  </div>
</template>