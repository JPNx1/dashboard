<script setup>
    import GoodMorningClock from '../components/GoodMorningClock.vue'
    import GoodMorningLogin from '../components/GoodMorningLogin.vue'
    import ToDoList from '../components/ToDoList.vue'
</script>

<template>
    <main>
        <h1>Good morning!</h1>
        <GoodMorningClock/>
        <GoodMorningLogin/>
        <ToDoList/>
    </main>
</template>
  
  <style>
  @media (min-width: 1024px) {
    .about {
      min-height: 100vh;
      display: flex;
      align-items: center;
    }
  }
  </style>
  