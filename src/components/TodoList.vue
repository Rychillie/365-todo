<template>
  <div class="todo-list" :class="{ 'todo-list__selected': selected }">
    <ul :style="{ width: `${todos.length * 100}%` }">
      <li
        v-for="todo in todos"
        :key="todo.name"
        :style="{ transform: `translate3d(-${currentIndex * 100}%, 0, 0)` }"
      >
        <Todo
          :todo="todo"
          :selected="selected && selected.todo === todo"
          @select="selectTodo"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import { mapState, mapMutation } from "vuex";
import Todo from "./Todo";

export default {
  components: {
    Todo,
  },
  computed: {
    ...mapState(["todos", "currentIndex", "selected"]),
  },
  methods: {
    ...mapMutation(["selectTodo", "nextTodo", "prevTodo"]),
  },
};
</script>

<style lang="scss">
.todo-list {
  padding: 0 32px;
  height: 400px;

  > ul,
  > ul > li {
    display: flex;
    height: 100%;
  }
  > ul > li {
    flex: 1;
  }
  .todo {
    border-radius: 8px;
    background-color: white;
  }
  .todo-list__selected {
    transform: scaleX(1.25);
  }
}
</style>
