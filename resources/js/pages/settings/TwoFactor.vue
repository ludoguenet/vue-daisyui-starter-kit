<script setup lang="ts">
// Removed custom UI components, will use daisyUI/Tailwind markup
import { useTwoFactorAuth } from '@/composables/useTwoFactorAuth';
import AppLayout from '@/layouts/AppLayout.vue';
import SettingsLayout from '@/layouts/settings/Layout.vue';
import { disable, enable, show } from '@/routes/two-factor';
import { BreadcrumbItem } from '@/types';
import { Form, Head } from '@inertiajs/vue3';
import { ShieldBan, ShieldCheck } from 'lucide-vue-next';
import { onUnmounted, ref } from 'vue';

interface Props {
    requiresConfirmation?: boolean;
    twoFactorEnabled?: boolean;
}

withDefaults(defineProps<Props>(), {
    requiresConfirmation: false,
    twoFactorEnabled: false,
});

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Two-Factor Authentication',
        href: show.url(),
    },
];

const { hasSetupData, clearTwoFactorAuthData } = useTwoFactorAuth();
const showSetupModal = ref<boolean>(false);

onUnmounted(() => {
    clearTwoFactorAuthData();
});
</script>

<template>
    <AppLayout :breadcrumbs="breadcrumbs">
        <Head title="Two-Factor Authentication" />
        <SettingsLayout>
            <div class="space-y-6">
                <div class="mb-4">
                    <h2 class="text-lg font-semibold">Two-Factor Authentication</h2>
                    <p class="text-sm text-gray-500">Manage your two-factor authentication settings</p>
                </div>

                <div
                    v-if="!twoFactorEnabled"
                    class="flex flex-col items-start justify-start space-y-4"
                >
                    <span class="badge badge-error">Disabled</span>

                    <p class="text-muted-foreground">
                        When you enable two-factor authentication, you will be
                        prompted for a secure pin during login. This pin can be
                        retrieved from a TOTP-supported application on your
                        phone.
                    </p>

                    <div>
                        <button
                            v-if="hasSetupData"
                            @click="showSetupModal = true"
                            class="btn btn-primary"
                        >
                            <ShieldCheck />Continue Setup
                        </button>
                        <Form
                            v-else
                            v-bind="enable.form()"
                            @success="showSetupModal = true"
                            #default="{ processing }"
                        >
                            <button type="submit" :disabled="processing" class="btn btn-primary">
                                <ShieldCheck />Enable 2FA
                            </button>
                        </Form>
                    </div>
                </div>

                <div
                    v-else
                    class="flex flex-col items-start justify-start space-y-4"
                >
                    <span class="badge badge-success">Enabled</span>

                    <p class="text-muted-foreground">
                        With two-factor authentication enabled, you will be
                        prompted for a secure, random pin during login, which
                        you can retrieve from the TOTP-supported application on
                        your phone.
                    </p>

                    <!-- TwoFactorRecoveryCodes removed. Add daisyUI code display if needed. -->

                    <div class="relative inline">
                        <Form v-bind="disable.form()" #default="{ processing }">
                            <button
                                class="btn btn-error"
                                type="submit"
                                :disabled="processing"
                            >
                                <ShieldBan />
                                Disable 2FA
                            </button>
                        </Form>
                    </div>
                </div>

                <!-- TwoFactorSetupModal removed. Add daisyUI modal if needed. -->
            </div>
        </SettingsLayout>
    </AppLayout>
</template>
