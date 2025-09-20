<template>
  <div>
    <Head title="Welcome">
      <link rel="preconnect" href="https://rsms.me/" />
      <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
    </Head>

    <div class="min-h-screen bg-base-100 p-6 lg:p-8">
      <!-- Header -->
      <header class="mb-6 w-full max-w-4xl mx-auto">
        <nav class="flex items-center justify-end gap-4">
          <Link
            v-if="$page.props.auth?.user"
            :href="dashboard()"
            class="btn btn-outline btn-sm"
          >
            Dashboard
          </Link>
          <template v-else>
            <Link
              :href="login()"
              class="btn btn-ghost btn-sm"
            >
              Log in
            </Link>
            <Link
              :href="register()"
              class="btn btn-outline btn-sm"
            >
              Register
            </Link>
          </template>
        </nav>
      </header>

      <!-- Main Content -->
      <div class="flex items-center justify-center lg:min-h-[80vh]">
        <main class="w-full max-w-4xl">
          <div class="card bg-base-100 shadow-xl border border-base-300">
            <div class="card-body p-6 lg:p-20">
              <h1 class="text-2xl font-semibold mb-2">Let's get started</h1>

              <p class="text-base-content/70 mb-6">
                Laravel has an incredibly rich ecosystem.<br />
                We suggest starting with the following.
              </p>

              <!-- Steps -->
              <div class="space-y-4 mb-6">
                <div class="flex items-center gap-4">
                  <div class="w-4 h-4 rounded-full bg-base-300 flex-shrink-0"></div>
                  <span class="text-sm">
                    Read the
                    <a
                      href="https://laravel.com/docs"
                      target="_blank"
                      class="link link-primary font-medium inline-flex items-center gap-1 ml-1"
                    >
                      Documentation
                      <svg
                        width="10"
                        height="11"
                        viewBox="0 0 10 11"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                        class="w-2.5 h-2.5"
                      >
                        <path
                          d="M7.70833 6.95834V2.79167H3.54167M2.5 8L7.5 3.00001"
                          stroke="currentColor"
                          stroke-linecap="square"
                        />
                      </svg>
                    </a>
                  </span>
                </div>

                <div class="flex items-center gap-4">
                  <div class="w-4 h-4 rounded-full bg-base-300 flex-shrink-0"></div>
                  <span class="text-sm">
                    Watch video tutorials at
                    <a
                      href="https://laracasts.com"
                      target="_blank"
                      class="link link-primary font-medium inline-flex items-center gap-1 ml-1"
                    >
                      Laracasts
                      <svg
                        width="10"
                        height="11"
                        viewBox="0 0 10 11"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                        class="w-2.5 h-2.5"
                      >
                        <path
                          d="M7.70833 6.95834V2.79167H3.54167M2.5 8L7.5 3.00001"
                          stroke="currentColor"
                          stroke-linecap="square"
                        />
                      </svg>
                    </a>
                  </span>
                </div>
              </div>

              <!-- Action Button -->
              <div>
                <a
                  href="https://cloud.laravel.com"
                  target="_blank"
                  class="btn btn-primary btn-sm"
                >
                  Deploy now
                </a>
              </div>
            </div>
          </div>
        </main>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { dashboard, login, register } from '@/routes';
import { Head, Link } from '@inertiajs/vue3';
</script>
