<template>
  <section id="architecture" class="border-t border-slate-100 dark:border-slate-800 py-20">
    <div class="max-w-7xl mx-auto px-6">
      <div class="mb-12">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 tracking-widest uppercase mb-2">System Design</p>
        <h2 class="text-2xl font-semibold text-slate-800 dark:text-slate-100">System Architecture</h2>
        <p class="mt-2 text-slate-500 dark:text-slate-400 max-w-2xl">
          A layered architecture approach where each component has a single responsibility. Requests flow predictably inward; responses flow outward.
        </p>
      </div>

      <!-- Request Lifecycle diagram -->
      <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-8 mb-6">
        <p class="mono text-xs text-slate-400 dark:text-slate-500 mb-6 uppercase tracking-wider">Request Lifecycle</p>
        <div class="overflow-x-auto">
          <div class="flex items-start gap-0 min-w-max">
            <!-- Client -->
            <div class="flex flex-col items-center">
              <div class="arch-box border-slate-300 dark:border-slate-600 text-slate-700 dark:text-slate-300 bg-white dark:bg-slate-900 min-w-[110px]">
                Client / Browser
              </div>
              <div class="mono text-xs text-slate-400 dark:text-slate-500 mt-2 text-center">Consumer</div>
            </div>
            <div class="arch-arrow mt-3">→</div>
            <!-- Middleware -->
            <div class="flex flex-col items-center">
              <div class="arch-box border-slate-300 dark:border-slate-600 text-slate-700 dark:text-slate-300 bg-white dark:bg-slate-900 min-w-[120px]">
                Middleware Layer
              </div>
              <div class="mono text-xs text-slate-400 dark:text-slate-500 mt-2 text-center">Auth · Rate Limit</div>
            </div>
            <div class="arch-arrow mt-3">→</div>
            <!-- Controller -->
            <div class="flex flex-col items-center">
              <div class="arch-box border-slate-800 dark:border-slate-400 text-slate-800 dark:text-slate-200 bg-slate-100 dark:bg-slate-700 min-w-[120px] font-medium">
                Controller
              </div>
              <div class="mono text-xs text-slate-400 dark:text-slate-500 mt-2 text-center">Route · Validate</div>
            </div>
            <div class="arch-arrow mt-3">→</div>
            <!-- Service -->
            <div class="flex flex-col items-center">
              <div class="arch-box border-slate-800 dark:border-slate-400 text-slate-800 dark:text-slate-200 bg-slate-100 dark:bg-slate-700 min-w-[120px] font-medium">
                Service Layer
              </div>
              <div class="mono text-xs text-slate-400 dark:text-slate-500 mt-2 text-center">Business Logic</div>
            </div>
            <div class="arch-arrow mt-3">→</div>
            <!-- Repository -->
            <div class="flex flex-col items-center">
              <div class="arch-box border-slate-300 dark:border-slate-600 text-slate-700 dark:text-slate-300 bg-white dark:bg-slate-900 min-w-[120px]">
                Repository
              </div>
              <div class="mono text-xs text-slate-400 dark:text-slate-500 mt-2 text-center">Data Access</div>
            </div>
            <div class="arch-arrow mt-3">→</div>
            <!-- Database -->
            <div class="flex flex-col items-center">
              <div class="arch-box border-slate-300 dark:border-slate-600 text-slate-700 dark:text-slate-300 bg-white dark:bg-slate-900 min-w-[110px]">
                Database
              </div>
              <div class="mono text-xs text-slate-400 dark:text-slate-500 mt-2 text-center">PostgreSQL · Redis</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Service & Repository Pattern -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-4">
        <!-- Service pattern -->
        <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6">
          <p class="mono text-xs text-slate-400 dark:text-slate-500 mb-4 uppercase tracking-wider">Service Pattern</p>
          <pre class="mono text-xs text-slate-600 dark:text-slate-300 leading-relaxed overflow-x-auto"><code>interface UserServiceInterface {
  findById(id: string): Promise&lt;User&gt;
  create(dto: CreateUserDto): Promise&lt;User&gt;
  update(id: string, dto: UpdateUserDto): Promise&lt;User&gt;
}

class UserService implements UserServiceInterface {
  constructor(
    private readonly repo: UserRepositoryInterface,
    private readonly cache: CacheService,
  ) {}

  async findById(id: string): Promise&lt;User&gt; {
    const cached = await this.cache.get(id)
    if (cached) return cached

    const user = await this.repo.findById(id)
    await this.cache.set(id, user, 300)
    return user
  }
}</code></pre>
        </div>

        <!-- Repository pattern -->
        <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-lg p-6">
          <p class="mono text-xs text-slate-400 dark:text-slate-500 mb-4 uppercase tracking-wider">Repository Pattern</p>
          <pre class="mono text-xs text-slate-600 dark:text-slate-300 leading-relaxed overflow-x-auto"><code>interface UserRepositoryInterface {
  findById(id: string): Promise&lt;User | null&gt;
  findAll(filter: UserFilter): Promise&lt;User[]&gt;
  save(user: User): Promise&lt;User&gt;
  delete(id: string): Promise&lt;void&gt;
}

class UserRepository implements UserRepositoryInterface {
  constructor(private db: Database) {}

  async findById(id: string): Promise&lt;User | null&gt; {
    return this.db.query(
      'SELECT * FROM users WHERE id = $1',
      [id]
    )
  }
}</code></pre>
        </div>
      </div>
    </div>
  </section>
</template>
