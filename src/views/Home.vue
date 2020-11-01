<template>
  <div class="home">
    <AppBar title="TODO" :left="bars" :right="search" />
    <Avatar />
    <Gradient />
    <TodoList />
  </div>
</template>

<script>
import AppBar from "../components/AppBar";
import Avatar from "../components/Avatar";
import Gradient from "../components/Gradient";
import TodoList from "../components/TodoList";

export default {
  components: {
    AppBar,
    Avatar,
    Gradient,
    TodoList,
  },
  data() {
    return {
      bars: "bars",
      search: "search",
    };
  },
};
</script>

<style lang="scss">
.home {
  height: 100%;
  width: 100%;
  overflow: hidden;
  color: white;
}
</style>
