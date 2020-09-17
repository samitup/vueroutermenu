<template>
  <div id="notes-table">
    <ul>
      <li v-for="notes of notes" :key="notes.id">
        {{notes.content}}
        </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'notes-table',
    props: {
      notes: Array,
    },
  }
</script>

<style scoped></style>