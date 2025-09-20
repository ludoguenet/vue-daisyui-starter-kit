<script setup lang="ts">
import RegisteredUserController from '@/actions/App/Http/Controllers/Auth/RegisteredUserController';
// Removed custom UI components, will use daisyUI/Tailwind markup
import AuthBase from '@/layouts/AuthLayout.vue';
import { login } from '@/routes';
import { Form, Head } from '@inertiajs/vue3';
import { LoaderCircle } from 'lucide-vue-next';
</script>

<template>
    <AuthBase
        title="Create an account"
        description="Enter your details below to create your account"
    >
        <Head title="Register" />

        <Form
            v-bind="RegisteredUserController.store.form()"
            :reset-on-success="['password', 'password_confirmation']"
            v-slot="{ errors, processing }"
            class="flex flex-col gap-6"
        >
            <div class="grid gap-6">
                <div class="grid gap-2">
                    <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
                    <input
                        id="name"
                        type="text"
                        required
                        autofocus
                        :tabindex="1"
                        autocomplete="name"
                        name="name"
                        placeholder="Full name"
                        class="input input-bordered w-full"
                    />
                    <span v-if="errors.name" class="text-error text-xs">{{ errors.name }}</span>
                </div>

                <div class="grid gap-2">
                    <label for="email" class="block text-sm font-medium text-gray-700">Email address</label>
                    <input
                        id="email"
                        type="email"
                        required
                        :tabindex="2"
                        autocomplete="email"
                        name="email"
                        placeholder="email@example.com"
                        class="input input-bordered w-full"
                    />
                    <span v-if="errors.email" class="text-error text-xs">{{ errors.email }}</span>
                </div>

                <div class="grid gap-2">
                    <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
                    <input
                        id="password"
                        type="password"
                        required
                        :tabindex="3"
                        autocomplete="new-password"
                        name="password"
                        placeholder="Password"
                        class="input input-bordered w-full"
                    />
                    <span v-if="errors.password" class="text-error text-xs">{{ errors.password }}</span>
                </div>

                <div class="grid gap-2">
                    <label for="password_confirmation" class="block text-sm font-medium text-gray-700">Confirm password</label>
                    <input
                        id="password_confirmation"
                        type="password"
                        required
                        :tabindex="4"
                        autocomplete="new-password"
                        name="password_confirmation"
                        placeholder="Confirm password"
                        class="input input-bordered w-full"
                    />
                    <span v-if="errors.password_confirmation" class="text-error text-xs">{{ errors.password_confirmation }}</span>
                </div>

                <button
                    type="submit"
                    class="btn btn-primary w-full"
                    tabindex="5"
                    :disabled="processing"
                    data-test="register-user-button"
                >
                    <LoaderCircle
                        v-if="processing"
                        class="h-4 w-4 animate-spin"
                    />
                    Create account
                </button>
            </div>

            <div class="text-center text-sm text-muted-foreground">
                Already have an account?
                <a
                    :href="login()"
                    class="link link-hover underline underline-offset-4"
                    :tabindex="6"
                >Log in</a>
            </div>
        </Form>
    </AuthBase>
</template>
