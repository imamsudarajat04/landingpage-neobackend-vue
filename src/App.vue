<script setup lang="ts">
import { ref, onMounted } from 'vue'
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import PhilosophySection from './components/PhilosophySection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ArchitectureSection from './components/ArchitectureSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import PerformanceSection from './components/PerformanceSection.vue'
import DevOpsSection from './components/DevOpsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ContactSection from './components/ContactSection.vue'

const isDark = ref(false)

onMounted(() => {
  isDark.value = document.documentElement.classList.contains('dark')
})

function toggleTheme() {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.setItem('theme', 'dark')
  } else {
    document.documentElement.classList.remove('dark')
    localStorage.setItem('theme', 'light')
  }
}
</script>

<template>
  <div class="min-h-screen bg-white dark:bg-slate-900 text-slate-800 dark:text-slate-100">
    <AppHeader :is-dark="isDark" @toggle-theme="toggleTheme" />
    <main>
      <HeroSection />
      <PhilosophySection />
      <SkillsSection />
      <ArchitectureSection />
      <ProjectsSection />
      <PerformanceSection />
      <DevOpsSection />
      <ExperienceSection />
      <ContactSection />
    </main>
    <footer class="border-t border-slate-200 dark:border-slate-700 py-8 text-center text-sm text-slate-400 dark:text-slate-500">
      <p>Built with Vue 3 + TailwindCSS — Focused on clarity and maintainability.</p>
    </footer>
  </div>
</template>
