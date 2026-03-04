<script setup lang="ts">
const experiences = [
  {
    role: 'Backend Developer',
    company: 'PT. Tech Startup Indonesia',
    duration: '2023 – Present',
    type: 'Full-time',
    achievements: [
      'Designed multi-tenant architecture serving 200+ company accounts with row-level security',
      'Reduced API response time by 40% via query optimization and Redis caching layer',
      'Built background job system processing 50k+ events/day with zero message loss',
      'Implemented OAuth2 with role-based access control across 8 user privilege levels',
    ],
  },
  {
    role: 'Junior Backend Developer',
    company: 'CV. Digital Agency',
    duration: '2022 – 2023',
    type: 'Full-time',
    achievements: [
      'Delivered REST APIs for 5 client projects using Laravel and PostgreSQL',
      'Integrated third-party payment gateways (Midtrans, Xendit) with webhook validation',
      'Wrote integration test suites covering critical business logic paths',
      'Migrated legacy MySQL queries to use parameterized statements throughout codebase',
    ],
  },
  {
    role: 'Backend Developer Intern',
    company: 'Software House',
    duration: '2021 – 2022',
    type: 'Internship',
    achievements: [
      'Built CRUD API endpoints and learned RESTful API design conventions',
      'Contributed to database schema design for an inventory management system',
      'Participated in code reviews and adopted Git workflow best practices',
    ],
  },
]
</script>

<template>
  <section id="experience" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Background</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">Experience</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          A timeline of technical roles and the meaningful engineering contributions in each.
        </p>
      </div>

      <!-- Vertical timeline -->
      <div class="flex flex-col">
        <div
          v-for="(exp, index) in experiences"
          :key="exp.company"
          class="relative flex gap-6"
        >
          <!-- Timeline connector -->
          <div class="flex flex-col items-center">
            <div class="timeline-dot bg-slate-300 dark:bg-slate-600 mt-1.5"></div>
            <div
              v-if="index < experiences.length - 1"
              class="w-px flex-1 bg-slate-200 dark:bg-slate-700 mt-2 mb-0"
            ></div>
          </div>

          <!-- Content -->
          <div class="pb-10 flex-1">
            <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6 hover:border-slate-300 dark:hover:border-slate-600 transition-colors duration-200">
              <div class="flex flex-wrap items-start justify-between gap-3 mb-4">
                <div>
                  <h3 class="text-sm font-semibold text-slate-800 dark:text-slate-100">{{ exp.role }}</h3>
                  <p class="text-sm text-slate-500 dark:text-slate-400 mt-0.5">{{ exp.company }}</p>
                </div>
                <div class="text-right flex flex-col items-end gap-1.5">
                  <span class="mono text-xs text-slate-500 dark:text-slate-400">{{ exp.duration }}</span>
                  <span class="mono text-xs px-2 py-0.5 bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-slate-400 dark:text-slate-500 rounded">{{ exp.type }}</span>
                </div>
              </div>
              <ul class="flex flex-col gap-2">
                <li
                  v-for="item in exp.achievements"
                  :key="item"
                  class="flex items-start gap-2 text-sm text-slate-500 dark:text-slate-400"
                >
                  <span class="mono text-slate-300 dark:text-slate-600 shrink-0 mt-0.5">—</span>
                  <span>{{ item }}</span>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
