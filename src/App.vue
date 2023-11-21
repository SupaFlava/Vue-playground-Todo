<script lang="ts">
import TaskList from "./components/TaskList.vue";
export default {
  name: "App",
  data() {
    return {
      newTask: "",
      tasks: [
        {
          id: 1,
          name: "Coding",
          complete: false,
        },
        {
          id: 2,
          name: "sports",
          complete: false,
        },
        {
          id: 3,
          name: "Grocories",
          complete: false,
        },
        {
          id: 4,
          name: "music",
          complete: false,
        },
      ],
    };
  },
  methods: {
    addTaskHandler() {
      if (!this.newTask) {
        return;
      } else {
        this.tasks.push(this.newTaskObject);
        this.newTask = "";
      }
    },
    toggleCompleteHandler(i) {
      this.tasks[i].complete = !this.tasks[i].complete;
    },
  },
  computed: {
    taskCount() {
      return this.tasks.length;
    },
    newTaskObject() {
      const newTaskObj = {
        id: this.tasks.length + 1,
        name: this.newTask,
        complete: false,
      };
      return newTaskObj;
    },
  },
  components: {
    TaskList,
  },
};
</script>

<template>
  <div class="w-full">
    <section id="input-area" class="m-auto w-1/2 px-10">
      <h1 class="text-3xl text-center font-semibold w-full">
        {{ taskCount }}{{ taskCount === 1 ? "Task" : "Tasks" }}
      </h1>
      <!--save input as a variable-->
      <form @submit.prevent>
        <input
          class="border-2 border-black rounded-md w-full px-2 text-center"
          type="text"
          v-model="newTask"
          :placeholder="'Enter Task # ' + (tasks.length + 1)"
        />
        <!--trigger action to add task-->

        <button
          @click="addTaskHandler"
          class="border-2 border-black rounded-md hidden"
        >
          Add Task
        </button>
      </form>
    </section>

    <TaskList @toggleComplete="toggleCompleteHandler" :tasks="tasks" />
  </div>
</template>

<style scoped></style>
