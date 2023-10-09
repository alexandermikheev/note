<template>
  <Form @onSubmit="handleSubmit" />
  <List @offEdit="handleOffEdit" @onEdit="handleOnEdit" @onRemove="handleRemove" :items="notes" />
</template>

<script>
import Form from '@/components/Notes/Form.vue'
import List from '@/components/Notes/List.vue'

export default {
  components: { Form, List },
  data() {
    return {
      notes: [
        {
          title: 'Learn Vue 3',
          tags: ['work'],
          edit: false,
        },
        {
          title: 'Finish course',
          tags: ['work', 'home'],
          edit: false,
        }
      ]
    }
  },
  mounted() {
    this.getNotes()
  },
  watch: {
    notes: {
      handler(updatedList) {
        localStorage.setItem('notes', JSON.stringify(updatedList))
      },
      deep: true
    }
  },
  methods: {
    // * get / set notes
    getNotes() {
      const localNotes = localStorage.getItem('notes')
      if (localNotes) {
        this.notes = JSON.parse(localNotes)
      }
    },
// * submit note
handleSubmit(title) {
  const note = {
    title: title,
    tags: [],
    edit: false
  }
  this.notes.push(note)
},
    // * remove note
    handleRemove(index) {
      this.notes.splice(index, 1)
    },
     handleOnEdit(idx){
      this.notes[idx].edit = true
    },
    handleOffEdit(idx){
       this.notes[idx].edit = false
    }
  }
}
</script>
