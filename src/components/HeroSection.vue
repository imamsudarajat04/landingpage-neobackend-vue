<template>
  <section id="hero" class="max-w-7xl mx-auto px-6 py-24 md:py-32">
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-center">
      
      <!-- Left Content -->
      <div class="lg:col-span-7">
        <!-- Label -->
        <div class="mb-6">
          <span class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase">Available for work</span>
        </div>

        <!-- Title -->
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-semibold leading-tight tracking-tight text-slate-800 dark:text-slate-100 mb-4">
          Backend Developer
        </h1>

        <p class="text-lg md:text-xl text-slate-500 dark:text-slate-400 font-normal leading-relaxed mb-6 max-w-2xl">
          Designing scalable, secure, and maintainable systems — focused on clean architecture, solid engineering principles, and long-term code quality.
        </p>

        <p class="text-slate-600 dark:text-slate-400 leading-relaxed mb-10 max-w-xl">
          I build backend systems that are easy to reason about, straightforward to extend, and reliable in production. My approach prioritizes structure over shortcuts and clarity over cleverness.
        </p>

        <!-- CTAs -->
        <div class="flex flex-wrap gap-3">
          <a
            href="#projects"
            class="inline-flex items-center gap-2 px-5 py-2.5 bg-slate-800 dark:bg-slate-100 text-white dark:text-slate-900 text-sm font-medium rounded-md hover:bg-slate-700 dark:hover:bg-slate-200 transition-colors duration-200"
          >
            View Projects
            <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
            </svg>
          </a>
          <a
            href="#architecture"
            class="inline-flex items-center gap-2 px-5 py-2.5 border border-slate-200 dark:border-slate-700 text-slate-700 dark:text-slate-300 text-sm font-medium rounded-md hover:border-slate-400 dark:hover:border-slate-500 hover:text-slate-900 dark:hover:text-slate-100 transition-colors duration-200"
          >
            View Architecture
          </a>
        </div>
      </div>

      <!-- Right Content (Image) -->
      <div class="lg:col-span-5 flex justify-center lg:justify-end mt-12 lg:mt-0 order-first lg:order-last">
        <div class="relative w-full max-w-md aspect-square rounded-3xl overflow-hidden shadow-2xl border border-slate-200/50 dark:border-slate-800/80 group transform transition-all hover:-translate-y-2 duration-500">
          <div class="absolute inset-0 bg-gradient-to-tr from-cyan-500/10 to-transparent z-10 mix-blend-overlay"></div>
          <img 
            src="/profile.png" 
            alt="Backend Developer Profile" 
            class="w-full h-full object-cover object-center scale-[1.02] group-hover:scale-105 transition-transform duration-700 ease-out"
          />
        </div>
      </div>

    </div>

    <!-- Stats row -->
    <div class="mt-20 pt-10 border-t border-slate-100 dark:border-slate-800 flex flex-wrap gap-10 md:gap-16">
      <div>
        <p class="text-3xl font-semibold text-slate-800 dark:text-slate-100">3+</p>
        <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">Years experience</p>
      </div>
      <div>
        <p class="text-3xl font-semibold text-slate-800 dark:text-slate-100">15+</p>
        <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">Projects shipped</p>
      </div>
      <div>
        <p class="text-3xl font-semibold text-slate-800 dark:text-slate-100">REST · gRPC</p>
        <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">API expertise</p>
      </div>
      <div>
        <p class="text-3xl font-semibold text-slate-800 dark:text-slate-100">Production</p>
        <p class="text-sm text-slate-500 dark:text-slate-400 mt-1">-ready systems</p>
      </div>
    </div>
  </section>
</template>
