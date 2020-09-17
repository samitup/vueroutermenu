<template>
  <div id="notes-form">
    <h1>Notes</h1>
    <input type="text" v-model="content" @keyup.enter="addNotes">
    <ul>
      <li v-for="notes of notes" :key="notes.id">
        {{notes.content}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "notes-form",
  data() {
    return {
      notes: [],
        content: "",
    };
  },
    methods: {
   async addNotes(){
      const res = await axios.post(`http://localhost:3001/notes`,{content : this.content})
      this.notes = [...this.notes, res.data]
      this.content = ''
    }
  }
 
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>