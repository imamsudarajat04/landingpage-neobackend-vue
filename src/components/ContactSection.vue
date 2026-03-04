<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: '',
})

const submitted = ref(false)

function handleSubmit() {
  // Placeholder submit handler
  submitted.value = true
  setTimeout(() => { submitted.value = false }, 3000)
}

const links = [
  {
    label: 'GitHub',
    href: 'https://github.com',
    icon: `<path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/>`,
  },
  {
    label: 'LinkedIn',
    href: 'https://linkedin.com',
    icon: `<path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>`,
  },
]
</script>

<template>
  <section id="contact" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">Get in Touch</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">Contact</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          Open to discussing backend engineering roles, architecture consulting, or technical collaboration.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <!-- Form -->
        <div class="lg:col-span-2">
          <form @submit.prevent="handleSubmit" class="flex flex-col gap-4">
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label for="name" class="mono text-xs text-slate-500 dark:text-slate-400 uppercase tracking-wider block mb-1.5">Name</label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  required
                  placeholder="Your name"
                  class="w-full px-3.5 py-2.5 text-sm bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-slate-800 dark:text-slate-100 placeholder-slate-400 dark:placeholder-slate-500 rounded-md focus:outline-none focus:border-slate-400 dark:focus:border-slate-500 transition-colors duration-200"
                >
              </div>
              <div>
                <label for="email" class="mono text-xs text-slate-500 dark:text-slate-400 uppercase tracking-wider block mb-1.5">Email</label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  required
                  placeholder="your@email.com"
                  class="w-full px-3.5 py-2.5 text-sm bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-slate-800 dark:text-slate-100 placeholder-slate-400 dark:placeholder-slate-500 rounded-md focus:outline-none focus:border-slate-400 dark:focus:border-slate-500 transition-colors duration-200"
                >
              </div>
            </div>
            <div>
              <label for="message" class="mono text-xs text-slate-500 dark:text-slate-400 uppercase tracking-wider block mb-1.5">Message</label>
              <textarea
                id="message"
                v-model="form.message"
                required
                rows="5"
                placeholder="What would you like to discuss?"
                class="w-full px-3.5 py-2.5 text-sm bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-slate-800 dark:text-slate-100 placeholder-slate-400 dark:placeholder-slate-500 rounded-md focus:outline-none focus:border-slate-400 dark:focus:border-slate-500 transition-colors duration-200 resize-y"
              ></textarea>
            </div>
            <div>
              <button
                type="submit"
                class="px-5 py-2.5 bg-slate-800 dark:bg-slate-100 text-white dark:text-slate-900 text-sm font-medium rounded-md hover:bg-slate-700 dark:hover:bg-slate-200 transition-colors duration-200"
              >
                <span v-if="!submitted">Send Message</span>
                <span v-else class="text-green-400 dark:text-green-600">Message sent ✓</span>
              </button>
            </div>
          </form>
        </div>

        <!-- Links panel -->
        <div class="flex flex-col gap-4">
          <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6">
            <p class="mono text-xs text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-4">Social & Code</p>
            <div class="flex flex-col gap-3">
              <a
                v-for="link in links"
                :key="link.label"
                :href="link.href"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center gap-3 text-sm text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-slate-100 transition-colors duration-200 group"
              >
                <svg class="w-4 h-4 shrink-0" fill="currentColor" viewBox="0 0 24 24" v-html="link.icon"></svg>
                <span>{{ link.label }}</span>
                <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3 ml-auto opacity-0 group-hover:opacity-100 transition-opacity duration-200" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/>
                </svg>
              </a>
            </div>
          </div>

          <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6">
            <p class="mono text-xs text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-2">Response time</p>
            <p class="text-sm text-slate-600 dark:text-slate-400 leading-relaxed">
              I typically respond within 1–2 business days. For urgent technical discussions, LinkedIn is faster.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
