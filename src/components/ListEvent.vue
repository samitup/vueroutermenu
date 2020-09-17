<template>
<div>
  <p class="homeText">
    Listaa tapahtumia
  </p>
  <notes-form @add:content="addNotes"/>
  <notes-table :notes="notes"/>
  </div>
</template>
<script>
import NotesTable from '@/components/NotesTable.vue'
import NotesForm from '@/components/NotesForm.vue'
import axios from 'axios';
export default {
  name: 'ListEvent',
  components: {
    NotesTable,
    NotesForm
  },
   data() {
    return {
      notes: [],
      content: ''
    }
  },
 
  async created() {
  try {
      const res = await axios.get(`http://localhost:3001/notes`)

      this.notes = res.data;
    } catch(e) {
      console.error(e)
    }
  },
};

</script>
<style scoped>
.homeText{
  font-size: 35px;
  color: red;
  text-align: center;
  position: relative;
  top:30px;
  text-shadow: 2px 2px 2px gray;
}
</style>