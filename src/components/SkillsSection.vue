<script setup lang="ts">
const categories = [
  {
    name: 'Languages',
    icon: '{ }',
    skills: ['PHP', 'TypeScript', 'Go', 'Python', 'Bash'],
  },
  {
    name: 'Frameworks',
    icon: '⚙',
    skills: ['Laravel', 'Express.js', 'Gin', 'FastAPI', 'NestJS'],
  },
  {
    name: 'Databases',
    icon: '⊟',
    skills: ['PostgreSQL', 'MySQL', 'MongoDB', 'SQLite', 'Elasticsearch'],
  },
  {
    name: 'Caching',
    icon: '≋',
    skills: ['Redis', 'Memcached', 'CDN Edge Cache', 'Query Cache'],
  },
  {
    name: 'DevOps',
    icon: '△',
    skills: ['Docker', 'GitHub Actions', 'CI/CD', 'Nginx', 'Linux'],
  },
  {
    name: 'Security',
    icon: '⊕',
    skills: ['JWT / OAuth2', 'RBAC', 'Rate Limiting', 'SQL Injection Prevention', 'CORS'],
  },
]
</script>

<template>
  <section id="skills" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Core Skills</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">Technical competencies</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400">Organized by domain — not just a flat list of buzzwords.</p>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
        <div
          v-for="cat in categories"
          :key="cat.name"
          class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-5 hover:border-slate-300 dark:hover:border-slate-600 transition-colors duration-200"
        >
          <div class="flex items-center gap-2.5 mb-4">
            <span class="mono text-slate-400 dark:text-slate-500 text-sm w-6">{{ cat.icon }}</span>
            <h3 class="text-sm font-semibold text-slate-700 dark:text-slate-200">{{ cat.name }}</h3>
          </div>
          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in cat.skills"
              :key="skill"
              class="mono text-xs px-2.5 py-1 bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-slate-600 dark:text-slate-300 rounded"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
