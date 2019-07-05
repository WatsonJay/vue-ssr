<template>
    <section class="real-app">
        <input
           type="text"
           class="add-input"
           autofocus="autofocus"
           placeholder="计划做什么事"
           @keyup.enter="addTodo"
        >
    </section>
</template>

<script>
    export default {
        name: "todo"
    }
</script>

<style lang="stylus" scoped>
.real-app {
    width 600px
    margin 0 auto
    box-shadow 0 0 5px #666
}
.add-input{
    position: relative;
    
}
</style>