<template>
  <nav class="filter-nav">
    <button @click="UpdateFilter('all')" :class="{ active: current === 'all' }">All Projects</button>
    <button @click="UpdateFilter('completed')" :class="{ active: current === 'completed' }">Completed</button>
    <button @click="UpdateFilter('ongoing')" :class="{ active: current === 'ongoing' }">Ongoing</button>
  </nav>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props: ['current'],
    methods: {
        UpdateFilter(by) {
            this.$emit('filterChange', by)
        }
    }
}
</script>

<style>
    .filter-nav button {
    background: none;
    border: none;
    color: rgb(128, 120, 120);
    outline: none;
    font-size: 12px;
    text-transform: uppercase;
    margin-right: 10px;
    letter-spacing: 1px;
    font-weight: bold;
    cursor: pointer;
  }
  .filter-nav button.active {
    color: rgb(255, 255, 255);
    border-bottom: 2px solid #00ce89;
    padding-bottom: 4px;
  }
</style>