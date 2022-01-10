<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
  import { defineComponent, ref } from "vue"
  import JobList from "@/components/JobList.vue"
  import { IJob } from "./types/job"
  import { OrderTerm } from "./types/OrderTerm"

  export default defineComponent({
    name: "App",
    components: { JobList },
    setup() {
      const jobs = ref<IJob[]>([
        {
          title: "farm worker",
          location: "london ranch",
          id: "1",
          salary: 2500,
        },
        {
          title: "quarry man",
          location: "death mountain",
          id: "2",
          salary: 1550,
        },
        {
          title: "flute player",
          location: "the lost woods",
          id: "3",
          salary: 4500,
        },
        {
          title: "fisherman",
          location: "lake hylia",
          id: "4",
          salary: 2000,
        },
        {
          title: "prison guard",
          location: "gerudo valley",
          id: "5",
          salary: 6500,
        },
      ])

      const order = ref<OrderTerm>("title")
      const handleClick = (term: OrderTerm) => {
        return (order.value = term)
      }

      return { jobs, handleClick, order }
    },
  })
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
    text-transform: capitalize;
  }
  header .title {
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
