<template>
  <div class="todolist-layout">
    <header>
      <slot name="header" :appName="appName"></slot>
    </header>

    <main>
      <slot name="main"></slot>
    </main>

    <footer>
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<script>
export default{
  name: "TodoListLayout",
  data(){
    return{
      appName: "Todo List avec des slots"
    }
  }
}
</script>