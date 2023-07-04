<template>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">

  <div class="speech_container mx-auto text-center">
    <i class="fas fa-microphone fa-3x mb-2 col-12"  :class="{ isListening: isListening}" @click="listen"></i>
    <p v-if="speechToText !== null" class="speechToText">{{ speechToText  }}</p>
  </div>
</template>

<script>
export default {
  props : {
    addNote : {
      type : Function,
      required : true
    },
    deleteNone : {
      type : Function,
      required : true
    },
    removeAllNotes : {
      type : Function,
      required : true
    }
  },
  data() {
    return {
      speechToText  : null,
      isListening   : false,
      recognition   : null
    }
  },
  methods : {
    listen() {

      console.log("started to listen");
      this.isListening = true;
      this.recognition.start();
    },
    record(event) {
      
      this.speechToText = event.results[0][0].transcript;
      this.isListening = false;
      this.addNote(this.speechToText)
      console.log(this.speechToText);
    }
  },
  mounted() {
    console.log("mounted");
    this.recognition = new webkitSpeechRecognition();
    this.recognition.lang = "tr";
    this.recognition.minDuration = 5000;
    this.recognition.onresult = this.record;
  }
}
</script>
  
<style scoped>

i {
  cursor: pointer;
}

.speechToText {
  margin-top: 10px;
}

.isListening {
  color: #c00201;
  transition: all 0.5s;
}
</style>