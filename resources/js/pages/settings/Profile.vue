<script setup lang="ts">
import ProfileController from '@/actions/App/Http/Controllers/Settings/ProfileController';
import { edit } from '@/routes/profile';
import { send } from '@/routes/verification';
import { Form, Head, Link, usePage } from '@inertiajs/vue3';

// Removed custom UI components, will use daisyUI/Tailwind markup
import AppLayout from '@/layouts/AppLayout.vue';
import SettingsLayout from '@/layouts/settings/Layout.vue';
import { type BreadcrumbItem } from '@/types';

interface Props {
    mustVerifyEmail: boolean;
    status?: string;
}

defineProps<Props>();

const breadcrumbItems: BreadcrumbItem[] = [
    {
        title: 'Profile settings',
        href: edit().url,
    },
];

const page = usePage();
const user = page.props.auth.user;
</script>

<template>
    <AppLayout :breadcrumbs="breadcrumbItems">
        <Head title="Profile settings" />

        <SettingsLayout>
            <div class="flex flex-col space-y-6">
                <div class="mb-4">
                    <h2 class="text-lg font-semibold">Profile information</h2>
                    <p class="text-sm text-gray-500">Update your name and email address</p>
                </div>

                <Form
                    v-bind="ProfileController.update.form()"
                    class="space-y-6"
                    v-slot="{ errors, processing, recentlySuccessful }"
                >
                    <div class="grid gap-2">
                        <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
                        <input
                            id="name"
                            class="input input-bordered w-full mt-1"
                            name="name"
                            :value="user.name"
                            required
                            autocomplete="name"
                            placeholder="Full name"
                        />
                        <span v-if="errors.name" class="text-error text-xs mt-2">{{ errors.name }}</span>
                    </div>

                    <div class="grid gap-2">
                        <label for="email" class="block text-sm font-medium text-gray-700">Email address</label>
                        <input
                            id="email"
                            type="email"
                            class="input input-bordered w-full mt-1"
                            name="email"
                            :value="user.email"
                            required
                            autocomplete="username"
                            placeholder="Email address"
                        />
                        <span v-if="errors.email" class="text-error text-xs mt-2">{{ errors.email }}</span>
                    </div>

                    <div v-if="mustVerifyEmail && !user.email_verified_at">
                        <p class="-mt-4 text-sm text-muted-foreground">
                            Your email address is unverified.
                            <Link
                                :href="send()"
                                as="button"
                                class="text-foreground underline decoration-neutral-300 underline-offset-4 transition-colors duration-300 ease-out hover:decoration-current! dark:decoration-neutral-500"
                            >
                                Click here to resend the verification email.
                            </Link>
                        </p>

                        <div
                            v-if="status === 'verification-link-sent'"
                            class="mt-2 text-sm font-medium text-green-600"
                        >
                            A new verification link has been sent to your email
                            address.
                        </div>
                    </div>

                    <div class="flex items-center gap-4">
                        <button
                            :disabled="processing"
                            data-test="update-profile-button"
                            class="btn btn-primary"
                        >Save</button>

                        <Transition
                            enter-active-class="transition ease-in-out"
                            enter-from-class="opacity-0"
                            leave-active-class="transition ease-in-out"
                            leave-to-class="opacity-0"
                        >
                            <p
                                v-show="recentlySuccessful"
                                class="text-sm text-neutral-600"
                            >
                                Saved.
                            </p>
                        </Transition>
                    </div>
                </Form>
            </div>

            <!-- DeleteUser component removed. If needed, replace with daisyUI modal/button implementation. -->
        </SettingsLayout>
    </AppLayout>
</template>
