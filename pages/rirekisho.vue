<template>
  <div>
    <input type="url" v-model="resumeLink" placeholder="Enter Resume URL" />
    <button @click="getResumeData">Get</button>

    <select v-model="selectedFormat">
      <option value="rirekisho">Formatted</option>
      <option value="rirekishoo">Plain</option>
    </select>

    <!-- Only show the component after data is fetched and the user clicks 'Get' -->
    <div v-if="resumeData">
      <component :is="selectedFormatComponent" :resumeData="resumeData" />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, defineAsyncComponent, computed } from 'vue'

const resumeLink = ref<string>('') // URL as a string
const resumeData = ref<any>(null) // Data fetched from the URL
const selectedFormat = ref<string>('rirekisho') // Default to 'rirekisho'

// Function to fetch resume data from the URL
const getResumeData = async () => {
  if (!resumeLink.value) {
    alert("Please enter a valid resume URL")
    return
  }

  try {
    const response = await fetch(resumeLink.value)
    if (!response.ok) {
      throw new Error("Failed to fetch data")
    }
    resumeData.value = await response.json() // Assuming JSON data

    // Load the appropriate component based on the selected format after fetching the data
    loadSelectedComponent()
  } catch (error) {
    console.error(error)
    alert("Error fetching the resume data")
  }
}

// Reactive variables for the components
let rirekishoComponent: any = null
let rirekishooComponent: any = null

// Dynamically load the components
const loadSelectedComponent = () => {
  // Dynamically import components based on dropdown selection
  if (selectedFormat.value === 'rirekisho') {
    rirekishoComponent = defineAsyncComponent(() => import('../components/rirekisho.vue'))
  } else {
    rirekishooComponent = defineAsyncComponent(() => import('../components/rirekishoo.vue'))
  }
}

// Compute which component to load based on selected format
const selectedFormatComponent = computed(() => {
  if (selectedFormat.value === 'rirekisho') {
    return rirekishoComponent
  } else {
    return rirekishooComponent
  }
})
</script>

<style scoped>
input {
  padding: 8px;
  margin-right: 10px;
}

button {
  padding: 8px 12px;
  background-color: #2980b9;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #3498db;
}

select {
  margin-top: 10px;
  padding: 5px;
}
</style>
