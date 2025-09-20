<script setup lang="ts">
import { ref } from 'vue';
const appearance = ref('system');
function setAppearance(mode: string) {
    appearance.value = mode;
    if (mode === 'system') {
        const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
        document.documentElement.setAttribute('data-theme', prefersDark ? 'dark' : 'light');
    } else {
        document.documentElement.setAttribute('data-theme', mode);
    }
}
import { Head } from '@inertiajs/vue3';

// Removed custom UI components, will use daisyUI/Tailwind markup
import { type BreadcrumbItem } from '@/types';

import AppLayout from '@/layouts/AppLayout.vue';
import SettingsLayout from '@/layouts/settings/Layout.vue';
import { edit } from '@/routes/appearance';

const breadcrumbItems: BreadcrumbItem[] = [
    {
        title: 'Appearance settings',
        href: edit().url,
    },
];
</script>

<template>
    <AppLayout :breadcrumbs="breadcrumbItems">

        <Head title="Appearance settings" />

        <SettingsLayout>
            <div class="space-y-6">
                <div class="mb-4">
                    <h2 class="text-lg font-semibold">Appearance settings</h2>
                    <p class="text-sm text-gray-500">Update your account's appearance settings</p>
                </div>
                <div class="w-full">
                    <div class="tabs tabs-boxed mb-6">
                        <input type="radio" name="appearance_tabs" class="tab" aria-label="System"
                            :checked="appearance === 'system'" @change="setAppearance('system')" />
                        <input type="radio" name="appearance_tabs" class="tab" aria-label="Light"
                            :checked="appearance === 'light'" @change="setAppearance('light')" />
                        <input type="radio" name="appearance_tabs" class="tab" aria-label="Dark"
                            :checked="appearance === 'dark'" @change="setAppearance('dark')" />
                    </div>
                    <div class="mt-6">
                        <div v-if="appearance === 'system'" class="p-4 rounded bg-base-200">
                            <span class="font-bold">System</span> mode uses your OS preference.
                        </div>
                        <div v-if="appearance === 'light'" class="p-4 rounded bg-base-200">
                            <span class="font-bold">Light</span> mode is always bright.
                        </div>
                        <div v-if="appearance === 'dark'" class="p-4 rounded bg-base-200">
                            <span class="font-bold">Dark</span> mode is easy on the eyes.
                        </div>
                    </div>
                </div>
            </div>
        </SettingsLayout>
    </AppLayout>
</template>
