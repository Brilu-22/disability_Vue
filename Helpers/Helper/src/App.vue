<template>
  <div class="app-container">
    <h1>School Management System (Accessibility Mode)</h1>
    
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
.app-container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 2rem;
  font-family: Arial, sans-serif;
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