<template>
  <div class="app-container">
    <h1><img src="./assets/CC grey logo.png" alt="logo">Code and Cloud School</h1>
    <h2>Accessibility Mode</h2>
    
    <!--Voice Control Component -->
    <VoiceControl @command-executed="handleVoiceCommand" />
    
    <!-- Video Player with Closed Captions -->
    <VideoPlayer 
      video-src="./sassets/ESP Now Boards Setup.mp4" 
      caption-src="/captions.vtt" 
    />
    
    <!-- Keyboard-Accessible Buttons -->
    <div class="action-buttons">
      <AccessibleButton label="Submit Assignment" />
      <AccessibleButton label="View Grades" />
    </div>
  </div>
</template>

<script setup>
import VoiceControl from './components/VoiceCommand.vue';
import VideoPlayer from './components/VideoPlayer.vue';
import AccessibleButton from './components/AccessibleButton.vue';

const handleVoiceCommand = (command) => {
  if (command.includes('submit')) {
    alert("Voice command: Submitting assignment!");
  } else if (command.includes('grades')) {
    alert("Voice command: Opening grades page!");
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@100..900&family=Quicksand:wght@300..700&display=swap');
.app-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 2rem;
  font-family: Arial, sans-serif;
}

img{
  width: 50px;
  height: 40px;
  margin-right: 10px;
  vertical-align: middle;
  display: inline-block;
  margin-left: 20px;
  margin-top: 20px;
  margin-bottom: 20px;
  padding: 0;
}
h1{
  font-family: "Lexend", sans-serif;
  font-optical-sizing: auto;
  font-size: 2rem;
  font-weight: 600;
  font-style: normal;
  color: #181818;
}

h2{
  font-family: "Lexend", sans-serif;
  font-optical-sizing: auto;
  font-size:1.2 rem;
  font-weight: 100;
  font-style: normal;
  color: #181818;
  padding-bottom: 20px;
  margin-left: 150px;
  
}

.action-buttons {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
}

/* Ensure focus visibility for keyboard users */
*:focus {
  outline: 3px solid #ff8c00;
}
</style>