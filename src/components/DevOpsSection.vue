<script setup lang="ts">
const devopsAreas = [
  {
    title: 'CI/CD Pipeline',
    icon: '⟳',
    items: [
      'GitHub Actions with branch protection rules',
      'Separate pipelines: lint → test → build → deploy',
      'Zero-downtime deploy via blue/green or rolling strategy',
      'Auto-rollback on health check failure',
    ],
  },
  {
    title: 'Docker & Containers',
    icon: '◻',
    items: [
      'Multi-stage Dockerfile: build stage + slim runtime image',
      'docker-compose for local development parity',
      '.env per environment; secrets via Docker secrets or Vault',
      'Non-root user inside container for security',
    ],
  },
  {
    title: 'Environment Separation',
    icon: '≡',
    items: [
      'dev / staging / production isolated environments',
      'Staging mirrors production configuration exactly',
      'Feature flags for controlled rollouts',
      'Database migrations run pre-deploy, not post',
    ],
  },
  {
    title: 'Monitoring & Logging',
    icon: '⊕',
    items: [
      'Structured JSON logging with request correlation IDs',
      'Error tracking with full stack traces and context',
      'Uptime monitoring with alerting thresholds',
      'DB slow query log piped to centralized logger',
    ],
  },
]
</script>

<template>
  <section id="devops" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Infrastructure</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">DevOps & Deployment</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          Deployments should be boring — predictable, automated, and reversible. Production parity with local development is non-negotiable.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div
          v-for="area in devopsAreas"
          :key="area.title"
          class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6 hover:border-slate-300 dark:hover:border-slate-600 transition-colors duration-200"
        >
          <div class="flex items-center gap-2.5 mb-4">
            <span class="mono text-slate-400 dark:text-slate-500">{{ area.icon }}</span>
            <h3 class="text-sm font-semibold text-slate-800 dark:text-slate-100">{{ area.title }}</h3>
          </div>
          <ul class="flex flex-col gap-2">
            <li
              v-for="item in area.items"
              :key="item"
              class="flex items-start gap-2 text-sm text-slate-500 dark:text-slate-400"
            >
              <span class="mono text-slate-300 dark:text-slate-600 mt-0.5 shrink-0">—</span>
              <span>{{ item }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>
