<template>
  <div>
    <button @click="startListening" class="voice-btn"> <!-- Fixed: Added @click handler -->
      🎤 {{ isListening ? "Listening..." : "Start Voice Control" }} <!-- Fixed: Added space & fixed typo -->
    </button>
    <p v-if="spokenText">You said: "{{ spokenText }}"</p>
    <div v-if="error" class="error">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isListening = ref(false);
const spokenText = ref("");
const error = ref("");

const startListening = () => {
  const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

  if (!SpeechRecognition) {
    error.value = "Speech recognition not supported in this browser.";
    return;
  }

  const recognition = new SpeechRecognition();
  recognition.continuous = false;
  recognition.interimResults = false;

  recognition.onstart = () => {
    isListening.value = true;
  };

  recognition.onresult = (event) => {
    const transcript = event.results[0][0].transcript;
    spokenText.value = transcript;
    executeCommand(transcript.toLowerCase());
  };

  recognition.onerror = (event) => {
    error.value = `Error: ${event.error}`;
    isListening.value = false;
  };

  recognition.onend = () => {
    isListening.value = false;
  };

  recognition.start();
};

const executeCommand = (command) => {
  if (command.includes("submit")) {
    alert("Form submitted via voice!");
  } else if (command.includes("navigate")) {
    alert("Navigating to home page...");
  } else if (command.includes("grades")){
    alert("Opening grades page...");
  } else {
    alert("Command not recognized.");
  }
};
</script>

<style>
.voice-btn {
  padding: 12px 24px;
  font-size: 16px;
  cursor: pointer;
  background: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
}
.error {
  color: red;
}
</style> 