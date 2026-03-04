<script setup lang="ts">
const optimizations = [
  {
    category: 'Query Optimization',
    icon: '⊟',
    items: [
      { label: 'Index strategy', detail: 'Composite indexes on frequently filtered columns. Analyzed query plans with EXPLAIN ANALYZE.' },
      { label: 'N+1 prevention', detail: 'Eager loading via ORM relationships. Query count assertions in integration tests.' },
      { label: 'Pagination', detail: 'Cursor-based pagination for large datasets; offset-based only for small, bounded result sets.' },
    ],
  },
  {
    category: 'Caching Strategy',
    icon: '≋',
    items: [
      { label: 'Read-through cache', detail: 'Redis as L2 cache. Cache key namespaced by entity + ID + version. TTL aligned to data freshness requirements.' },
      { label: 'Cache invalidation', detail: 'Event-driven invalidation on write operations. Avoid stale reads via consistent tag-based purge.' },
      { label: 'HTTP cache headers', detail: 'ETag + Last-Modified for GET endpoints. Reduces bandwidth and server compute on unchanged resources.' },
    ],
  },
  {
    category: 'Background Jobs',
    icon: '△',
    items: [
      { label: 'Async processing', detail: 'Email, PDF export, and notification delivery offloaded to queues. API responds immediately.' },
      { label: 'Job reliability', detail: 'At-least-once delivery with idempotency keys. Failed jobs retry with exponential backoff.' },
      { label: 'Queue monitoring', detail: 'Queue depth and failure rate tracked. Alerting on dead letter queue growth.' },
    ],
  },
]

const metrics = [
  { label: 'P95 API Latency', value: '< 120ms', context: 'Under 500 RPS' },
  { label: 'DB Query Reduction', value: '60%', context: 'via Redis caching' },
  { label: 'Cache Hit Rate', value: '~85%', context: 'Read-heavy endpoints' },
  { label: 'Queue Throughput', value: '2k/min', context: '4 worker processes' },
]
</script>

<template>
  <section id="performance" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Optimization</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">Performance & Optimization</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          Performance decisions are made based on profiling, not assumption. Every optimization has a measured rationale.
        </p>
      </div>

      <!-- Metrics row -->
      <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
        <div
          v-for="m in metrics"
          :key="m.label"
          class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-5"
        >
          <p class="text-xl font-semibold text-slate-800 dark:text-slate-100 mono">{{ m.value }}</p>
          <p class="text-sm font-medium text-slate-600 dark:text-slate-300 mt-1">{{ m.label }}</p>
          <p class="text-xs text-slate-400 dark:text-slate-500 mt-0.5">{{ m.context }}</p>
        </div>
      </div>

      <!-- Detail cards -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
        <div
          v-for="opt in optimizations"
          :key="opt.category"
          class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6"
        >
          <div class="flex items-center gap-2 mb-5">
            <span class="mono text-slate-400 dark:text-slate-500">{{ opt.icon }}</span>
            <h3 class="text-sm font-semibold text-slate-800 dark:text-slate-100">{{ opt.category }}</h3>
          </div>
          <div class="flex flex-col gap-4">
            <div v-for="item in opt.items" :key="item.label">
              <p class="text-xs font-medium text-slate-700 dark:text-slate-300 mb-1">{{ item.label }}</p>
              <p class="text-xs text-slate-500 dark:text-slate-400 leading-relaxed">{{ item.detail }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
