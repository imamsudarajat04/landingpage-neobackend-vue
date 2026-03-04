<script setup lang="ts">
const projects = [
  {
    name: 'Multi-Tenant SaaS API',
    problem: 'A growing SaaS product needed to support multiple isolated tenants with role-based access control, custom billing cycles, and usage-based rate limiting — all from a single codebase.',
    architecture: 'Row-level security in PostgreSQL for tenant isolation. Middleware chain for auth → tenant resolution → rate limiting → RBAC check. Separate schema-per-tenant migration system.',
    stack: ['Laravel', 'PostgreSQL', 'Redis', 'Docker', 'GitHub Actions'],
    performance: 'p95 response time <120ms under 500 concurrent users. Redis-backed session store reduced DB load by ~60%.',
    security: 'JWT with short-lived access tokens + refresh token rotation. RBAC enforced at middleware level, not controller. SQL queries parameterized throughout.',
    github: 'https://github.com',
  },
  {
    name: 'Real-Time Notification Engine',
    problem: 'A workplace platform needed push notifications, email digests, and in-app alerts across 10k+ users without blocking the main API response time.',
    architecture: 'Event-driven: API dispatches events to a Redis queue. Worker processes pick up jobs and fan out to channels (FCM, SMTP, WebSocket). Channel adapters are pluggable.',
    stack: ['Node.js', 'TypeScript', 'Redis (Bull)', 'PostgreSQL', 'WebSocket'],
    performance: 'Notification delivery under 500ms P90. Queue throughput: ~2,000 events/min with 4 workers. Zero message loss on worker restart.',
    security: 'Notification payloads do not include sensitive data — only IDs. Client fetches full records via authenticated API.',
    github: 'https://github.com',
  },
  {
    name: 'REST API Gateway — HR System',
    problem: 'Legacy monolith HR system exposed inconsistent endpoints, with no versioning, no auth standard, and no rate limiting. Needed modernization without full rewrite.',
    architecture: 'Strangler fig pattern. New Laravel API gateway sits in front. Routes new features to new services, legacy routes proxy to old system. Incremental migration.',
    stack: ['Laravel', 'PHP', 'MySQL', 'Redis', 'Nginx'],
    performance: 'Response caching reduced database queries by 40% for read-heavy endpoints. Connection pooling via PgBouncer for write paths.',
    security: 'OAuth2 with Laravel Passport. Rate limiting per client_id. Input validation on all request bodies before any DB operation.',
    github: 'https://github.com',
  },
]
</script>

<template>
  <section id="projects" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Selected Work</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">Projects</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          Each project is documented the way I would document it internally — with the problem, the architecture decision, and the tradeoffs.
        </p>
      </div>

      <div class="flex flex-col gap-4">
        <div
          v-for="project in projects"
          :key="project.name"
          class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-7 hover:border-slate-300 dark:hover:border-slate-600 transition-colors duration-200"
        >
          <!-- Header row -->
          <div class="flex items-start justify-between gap-4 mb-5">
            <h3 class="text-base font-semibold text-slate-800 dark:text-slate-100">{{ project.name }}</h3>
            <a
              :href="project.github"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center gap-1.5 mono text-xs text-slate-500 dark:text-slate-400 hover:text-slate-800 dark:hover:text-slate-100 transition-colors duration-200 shrink-0"
            >
              <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/>
              </svg>
              GitHub
            </a>
          </div>

          <!-- 4-column detail grid -->
          <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-5">
            <div>
              <p class="mono text-xs text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Problem</p>
              <p class="text-sm text-slate-600 dark:text-slate-400 leading-relaxed">{{ project.problem }}</p>
            </div>
            <div>
              <p class="mono text-xs text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Architecture</p>
              <p class="text-sm text-slate-600 dark:text-slate-400 leading-relaxed">{{ project.architecture }}</p>
            </div>
            <div>
              <p class="mono text-xs text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Performance</p>
              <p class="text-sm text-slate-600 dark:text-slate-400 leading-relaxed">{{ project.performance }}</p>
            </div>
            <div>
              <p class="mono text-xs text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Security</p>
              <p class="text-sm text-slate-600 dark:text-slate-400 leading-relaxed">{{ project.security }}</p>
            </div>
          </div>

          <!-- Tech stack -->
          <div class="mt-5 pt-5 border-t border-slate-200 dark:border-slate-700 flex flex-wrap gap-2">
            <span
              v-for="tech in project.stack"
              :key="tech"
              class="mono text-xs px-2 py-0.5 bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-700 text-slate-500 dark:text-slate-400 rounded"
            >{{ tech }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
