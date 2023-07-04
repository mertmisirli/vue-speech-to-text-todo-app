<template>

  <div id="app">
    <div id="appContainer">
      <appHeader></appHeader>
      <speech
      :noteItem="note"
      :addNote="addNote"
      :deleteNote="deleteNode"
      :removeAllNotes="removeAllNotes" 
      ></speech>

      <noteItem 
      v-for="note in notes" :key="note" :noteItem="note">
    </noteItem>
    </div>
  </div>

</template>

<script>
import appHeader from "@/components/appHeader"
import noteItem from "@/components/noteItem"
import speech from "@/components/speech"

export default {
  components : {
    appHeader,
    noteItem,
    speech
  },
  data() {
    return {
      notes : [
        { id : 1, note : "note 1"},
        { id : 2, note : "note 2"},
        { id : 3, note : "note 3"},
        { id : 4, note : "note 4"},
      ]
    }
  },
  methods: {
    addNote(note) {
      this.notes.push({
        id : this.notes.length + 1,
        note : note
      });
    },

    deleteNote(id) {
      this.notes.splice(this.notes.findIndex(n => n.id == id), 1);
    },

    removeAllNotes() {
      this.notes = [];
    }
  }
}

</script>