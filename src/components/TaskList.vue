<script>
export default {
  name: "TaskList",
  props: {
    tasks: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    toggleCompleteHandler(i) {
      this.$emit("toggleComplete", i);
    },
  },
};
</script>
<template>
  <section id="task-list" class="w-1/2 flex mx-12">
    <ul class="m-auto">
      <li
        :class="{
          'cursor-pointer': true,
          'line-through': task.complete,
        }"
        @click="toggleCompleteHandler(i)"
        v-for="(task, i) in tasks"
        :key="i"
      >
        {{ task.id }} {{ task.name }}
      </li>
    </ul>
  </section>
</template>
<style></style>
