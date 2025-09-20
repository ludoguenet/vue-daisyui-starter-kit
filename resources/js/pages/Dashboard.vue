<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { dashboard } from '@/routes';
import { type BreadcrumbItem } from '@/types';
import { Head } from '@inertiajs/vue3';

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: dashboard().url,
    },
];
</script>

<template>
    <Head title="Dashboard" />

        <AppLayout :breadcrumbs="breadcrumbs">
            <div class="p-6 space-y-8">
                <h1 class="text-2xl font-bold mb-4">daisyUI Component Showcase</h1>
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">

                    <!-- Actions -->
                    <div>
                        <h2 class="font-semibold mb-2">Actions</h2>
                        <button class="btn btn-primary">Primary Button</button>
                        <button class="btn btn-secondary ml-2">Secondary Button</button>
                        <button class="btn btn-outline ml-2">Outline Button</button>
                        <button class="btn btn-accent ml-2">Accent Button</button>
                        <button class="btn btn-ghost ml-2">Ghost Button</button>
                        <button class="btn btn-link ml-2">Link Button</button>
                    </div>
                    <!-- Data display -->
                    <div>
                        <h2 class="font-semibold mb-2">Data display</h2>
                        <div class="stats shadow">
                            <div class="stat">
                                <div class="stat-title">Downloads</div>
                                <div class="stat-value">31K</div>
                                <div class="stat-desc">Jan 1st - Feb 1st</div>
                            </div>
                            <div class="stat">
                                <div class="stat-title">Users</div>
                                <div class="stat-value">4,200</div>
                                <div class="stat-desc">↗︎ 400 (22%)</div>
                            </div>
                        </div>
                        <progress class="progress progress-primary w-full mt-4" value="70" max="100"></progress>
                    </div>
                    <!-- Navigation -->
                    <div>
                        <h2 class="font-semibold mb-2">Navigation</h2>
                        <div class="menu bg-base-200 rounded-box p-2">
                            <ul>
                                <li><a>Dashboard</a></li>
                                <li><a>Profile</a></li>
                                <li><a>Settings</a></li>
                            </ul>
                        </div>
                        <div class="tabs tabs-boxed mt-4">
                            <a class="tab tab-active">Tab 1</a>
                            <a class="tab">Tab 2</a>
                            <a class="tab">Tab 3</a>
                        </div>
                    </div>
                    <!-- Feedback -->
                    <div>
                        <h2 class="font-semibold mb-2">Feedback</h2>
                        <div class="alert alert-success mb-2">Success! Your action was completed.</div>
                        <div class="alert alert-error mb-2">Error! Something went wrong.</div>
                        <div class="alert alert-warning mb-2">Warning! Check your input.</div>
                        <div class="alert alert-info">Info! This is an informational message.</div>
                    </div>
                    <!-- Data input -->
                    <div>
                        <h2 class="font-semibold mb-2">Data input</h2>
                        <input type="text" placeholder="Type here" class="input input-bordered w-full mb-2" />
                        <input type="checkbox" class="checkbox mr-2" /> Checkbox
                        <input type="radio" name="radio-1" class="radio mr-2" checked /> Radio
                        <input type="range" min="0" max="100" value="50" class="range w-full mt-2" />
                        <select class="select select-bordered w-full mt-2">
                            <option disabled selected>Pick one</option>
                            <option>Option 1</option>
                            <option>Option 2</option>
                        </select>
                    </div>
                    <!-- Layout -->
                    <div>
                        <h2 class="font-semibold mb-2">Layout</h2>
                        <div class="card w-full bg-base-100 shadow-xl">
                            <div class="card-body">
                                <h2 class="card-title">Card title</h2>
                                <p>Card content goes here.</p>
                                <div class="card-actions justify-end">
                                    <button class="btn btn-primary">Action</button>
                                </div>
                            </div>
                        </div>
                        <div class="mockup-window border bg-base-300 mt-4">
                            <div class="flex justify-center px-4 py-8 bg-base-200">Mockup window content</div>
                        </div>
                    </div>
                    <!-- Mockup -->
                    <div>
                        <h2 class="font-semibold mb-2">Mockup</h2>
                        <div class="mockup-code">
                            <pre data-prefix="$"><code>npm install daisyui</code></pre>
                            <pre data-prefix=">"><code>Done!</code></pre>
                        </div>
                    </div>
                </div>
            </div>
        </AppLayout>
</template>
