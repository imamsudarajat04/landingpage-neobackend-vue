<script setup lang="ts">
const principles = [
  {
    title: 'Clean Architecture',
    icon: '◈',
    desc: 'Strict separation between domain, application, infrastructure, and interface layers. Dependencies always point inward toward the domain.',
  },
  {
    title: 'SOLID Principles',
    icon: '◇',
    desc: 'Single responsibility, open/closed, Liskov substitution, interface segregation, and dependency inversion — applied consistently across the codebase.',
  },
  {
    title: 'Separation of Concerns',
    icon: '⊞',
    desc: 'Each module has one reason to change. Business logic stays out of controllers; data access stays out of services.',
  },
  {
    title: 'Maintainability First',
    icon: '◎',
    desc: 'Code that a new developer can understand in 15 minutes. Explicit over implicit, readable over clever.',
  },
  {
    title: 'API Contract Design',
    icon: '≡',
    desc: 'APIs designed from the consumer perspective. Versioned, documented, and stable — breaking changes are treated as architectural decisions.',
  },
  {
    title: 'Fail-Safe Defaults',
    icon: '⊗',
    desc: 'Systems designed to fail gracefully. Errors are typed, logged, and never silently swallowed. Health checks and circuit breakers are standard.',
  },
]
</script>

<template>
  <section id="philosophy" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Engineering Philosophy</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">How I think about systems</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          Good backend engineering is about making correct decisions before writing code. These principles guide every design choice I make.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        <div
          v-for="p in principles"
          :key="p.title"
          class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6 hover:border-slate-400 dark:hover:border-slate-500 transition-colors duration-200"
        >
          <div class="mono text-slate-400 dark:text-slate-500 text-lg mb-3">{{ p.icon }}</div>
          <h3 class="text-sm font-semibold text-slate-800 dark:text-slate-100 mb-2">{{ p.title }}</h3>
          <p class="text-sm text-slate-500 dark:text-slate-400 leading-relaxed">{{ p.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
