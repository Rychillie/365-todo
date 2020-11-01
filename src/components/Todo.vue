<template>
  <div class="todo" :class="{ todo__selected: selected }">
    <div class="todo_head" @click="handleClick">
      <div class="todo_icon" style="{ color }">
        <i :class="['fa', `fa-${todo.icon}`]"></i>
      </div>
      <div class="todo_menu">
        <i class="fa fa-ellipsis-v"></i>
      </div>
      <div class="todo_body">
        <p class="todo_tips">{{ todo.tasks.length }} Tasks</p>
        <h3 class="todo_title">{{ todo.name }}</h3>
        <div class="todo_progress">
          <span class="todo_progress_line">
            <i style="{ width: progress, backgroundImage: ProgressColor }"></i>
          </span>
          <span class="todo_progress_num">{{ progress }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//import { today, tomorrow } from "../shared/index";
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    selected: {
      type: Boolean,
    },
  },
  computed: {
    color() {
      return this.todo.colors[0];
    },
    progress() {
      const totalCount = this.todo.tasks.filter((t) => !t.deleted).length;
      const doneCount = this.todo.tasks.filter((t) => !t.deleted && t.done)
        .length;
      return `${Math.round((doneCount / totalCount) * 100)}%`;
    },
    progressColor() {
      const colorBottom = `color-stop(30%, ${this.todo.colors[0]})`;
      const colorTop = `to(${this.todo.colors[1]})`;
      return `-webkit-gradient(linear, left bottom, right bottom, ${colorBottom}, ${colorTop})`;
    },
  },
};
</script>
