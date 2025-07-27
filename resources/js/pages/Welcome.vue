<template>
    <div
        :class="[
            'flex min-h-screen items-center justify-center p-2 transition-all duration-500 sm:p-4 lg:p-6',
            theme === 'dark'
                ? 'bg-gradient-to-br from-purple-600 via-purple-700 to-purple-900'
                : 'bg-gradient-to-br from-blue-400 via-blue-500 to-blue-600',
        ]"
    >
        <div class="absolute top-3 left-1/2 z-10 -translate-x-1/2 transform sm:top-4 lg:top-6">
            <div class="flex rounded-full bg-black/30 p-0.5 backdrop-blur-sm sm:p-1">
                <button
                    :class="[
                        'rounded-full px-2 py-1 text-xs font-medium transition-all duration-200 sm:px-3 sm:py-1.5 sm:text-sm lg:px-4 lg:py-2',
                        activeTab === 'waitlist' ? (theme === 'dark' ? 'bg-white text-black' : 'bg-black text-white') : 'text-gray-400',
                    ]"
                    @click="activeTab = 'waitlist'"
                >
                    Waitlist
                </button>
                <button
                    :class="[
                        'rounded-full px-2 py-1 text-xs font-medium transition-all duration-200 sm:px-3 sm:py-1.5 sm:text-sm lg:px-4 lg:py-2',
                        activeTab === 'manifesto' ? (theme === 'dark' ? 'bg-white text-black' : 'bg-black text-white') : 'text-gray-400',
                    ]"
                    @click="activeTab = 'manifesto'"
                >
                    Manifesto
                </button>
            </div>
        </div>

        <div
            :class="[
                'mx-auto w-full max-w-xs rounded-2xl border p-4 shadow-2xl backdrop-blur-sm transition-all duration-500 sm:max-w-sm sm:rounded-3xl sm:p-6 md:max-w-md md:p-8 lg:max-w-lg xl:max-w-xl',
                theme === 'dark' ? 'border-gray-800/50 bg-gray-900/90' : 'border-white/50 bg-white/90',
            ]"
        >
            <div class="mb-6 text-center sm:mb-8">
                <div
                    :class="[
                        'flex items-center justify-center gap-1 text-xl font-bold sm:gap-2 sm:text-2xl lg:text-3xl',
                        theme === 'dark' ? 'text-white' : 'text-gray-900',
                    ]"
                >
                    <span>zippr.site</span>
                </div>
            </div>

            <!-- Waitlist Content -->
            <div v-if="activeTab === 'waitlist'">
                <div class="mb-6 text-center sm:mb-8">
                    <h1
                        :class="[
                            'mb-4 text-2xl leading-tight font-bold sm:mb-6 sm:text-2xl lg:text-3xl',
                            theme === 'dark' ? 'text-white' : 'text-gray-900',
                        ]"
                    >
                        Clean, simple links. No API required.
                    </h1>
                    <p
                        :class="[
                            'px-2 text-xs leading-relaxed sm:px-0 sm:text-sm lg:text-base',
                            theme === 'dark' ? 'text-gray-300' : 'text-gray-600',
                        ]"
                    >
                        Zippr.site is a fast and reliable URL shortener that transforms long, messy links into clean, trackable ones. Built entirely
                        with Laravel controllers and Laravel Reverb—no APIs involved. Join the waitlist and be the first to try it in 2025.
                    </p>
                </div>

                <div class="mb-6 sm:mb-8">
                    <div class="block space-y-3 sm:hidden">
                        <input
                            v-model="email"
                            type="email"
                            placeholder="Your work email"
                            :class="[
                                'w-full rounded-full border-2 px-4 py-3 text-sm transition-all duration-200 outline-none',
                                theme === 'dark'
                                    ? 'border-gray-600 bg-gray-800/80 text-white placeholder-gray-400 focus:border-white focus:bg-gray-800'
                                    : 'border-gray-300 bg-white/80 text-gray-900 placeholder-gray-500 focus:border-gray-900 focus:bg-white',
                            ]"
                        />
                        <button
                            @click="joinWaitlist"
                            type="button"
                            :class="[
                                'w-full rounded-full py-3 text-sm font-semibold transition-all duration-200 hover:scale-[1.02] active:scale-95',
                                theme === 'dark' ? 'bg-white text-black hover:bg-gray-100' : 'bg-gray-900 text-white hover:bg-gray-800',
                            ]"
                        >
                            Join waitlist
                        </button>
                    </div>

                    <div
                        :class="[
                            'hidden overflow-hidden rounded-full border-2 shadow-lg transition-all duration-200 sm:flex',
                            theme === 'dark'
                                ? 'border-gray-600 bg-gray-800/80 focus-within:border-white focus-within:shadow-white/20'
                                : 'border-gray-300 bg-white/80 focus-within:border-gray-900 focus-within:shadow-gray-900/20',
                        ]"
                    >
                        <input
                            v-model="email"
                            type="email"
                            placeholder="Your work email"
                            :class="[
                                'flex-1 bg-transparent px-4 py-3 text-sm outline-none placeholder:text-sm sm:px-6 sm:py-4',
                                theme === 'dark' ? 'text-white placeholder-gray-400' : 'text-gray-900 placeholder-gray-500',
                            ]"
                        />
                        <button
                            @click="joinWaitlist"
                            type="button"
                            :class="[
                                'px-4 py-3 text-sm font-semibold whitespace-nowrap transition-all duration-200 hover:scale-105 active:scale-95 sm:px-6 sm:py-4 lg:px-8',
                                theme === 'dark' ? 'bg-white text-black hover:bg-gray-100' : 'bg-gray-900 text-white hover:bg-gray-800',
                            ]"
                        >
                            Join waitlist
                        </button>
                    </div>
                </div>
            </div>

            <div v-if="activeTab === 'manifesto'">
                <div
                    :class="[
                        'mb-6 space-y-4 text-xs leading-relaxed sm:mb-8 sm:space-y-6 sm:text-sm lg:text-base',
                        theme === 'dark' ? 'text-gray-300' : 'text-gray-600',
                    ]"
                >
                    <p>
                        Zippr.site was built for developers who want full control without the complexity of external APIs. It's a powerful URL
                        shortening platform that delivers speed, analytics, and branded links—all from a Laravel-first, real-time backend powered by
                        Laravel Reverb.
                    </p>
                    <p>
                        In a world of bloated platforms and scattered integrations, we chose simplicity, reliability, and transparency. Zippr.site
                        runs lean and fast—just like the links it creates. No vendor lock-in, no dependencies you don’t own.
                    </p>
                    <p>Whether you're tracking campaigns or cleaning up your links, Zippr.site is the infrastructure you control.</p>
                </div>

                <div class="mb-4 sm:mb-6">
                    <div
                        :class="[
                            'font-signature mb-1 inline-block skew-x-6 text-2xl sm:mb-2 sm:text-3xl lg:text-4xl',
                            theme === 'dark' ? 'text-white' : 'text-gray-900',
                        ]"
                    >
                        Rollen A.
                    </div>

                    <div :class="['text-xs sm:text-sm', theme === 'dark' ? 'text-gray-400' : 'text-gray-500']">
                        Rollen Asistores
                        <span :class="theme === 'dark' ? 'text-gray-500' : 'text-gray-400'"> CEO @ zippr.site </span>
                    </div>
                </div>
            </div>

            <!-- Footer - Super responsive layout -->
            <div
                :class="['border-t pt-3 text-xs transition-all duration-200 sm:pt-4', theme === 'dark' ? 'border-gray-700/50' : 'border-gray-300/50']"
            >
                <!-- Mobile: Stacked layout -->
                <div class="flex flex-col space-y-3 sm:hidden">
                    <div :class="['text-center text-xs', theme === 'dark' ? 'text-gray-500' : 'text-gray-600']">
                        Follow Zippr.site on
                        <a href="#" class="text-blue-400 underline hover:text-blue-300">X</a>
                        and
                        <a href="#" class="text-blue-400 underline hover:text-blue-300">Discord</a>
                    </div>

                    <div class="flex items-center justify-center gap-2 sm:gap-3">
                        <button
                            @click="theme = 'dark'"
                            type="button"
                            :class="[
                                'cursor-pointer rounded px-2 py-1 text-xs font-medium transition-all hover:opacity-80',
                                theme === 'dark'
                                    ? theme === 'dark'
                                        ? 'bg-white/10 text-white'
                                        : 'bg-gray-900/10 text-gray-900'
                                    : theme === 'dark'
                                      ? 'text-gray-400'
                                      : 'text-gray-500',
                            ]"
                        >
                            Dark
                        </button>
                        <div class="relative h-4 w-8 cursor-pointer rounded-full bg-gray-600" @click="toggleTheme">
                            <div
                                :class="[
                                    'absolute top-0.5 h-3 w-3 rounded-full bg-white transition-transform duration-200',
                                    theme === 'dark' ? 'left-0.5' : 'left-4',
                                ]"
                            ></div>
                        </div>
                        <button
                            @click="theme = 'light'"
                            type="button"
                            :class="[
                                'cursor-pointer rounded px-2 py-1 text-xs font-medium transition-all hover:opacity-80',
                                theme === 'light'
                                    ? theme === 'dark'
                                        ? 'bg-white/10 text-white'
                                        : 'bg-gray-900/10 text-gray-900'
                                    : theme === 'dark'
                                      ? 'text-gray-400'
                                      : 'text-gray-500',
                            ]"
                        >
                            Light
                        </button>
                    </div>
                </div>

                <!-- Desktop: Inline layout -->
                <div class="hidden items-center justify-between sm:flex">
                    <div :class="['text-xs', theme === 'dark' ? 'text-gray-500' : 'text-gray-600']">
                        Follow Zippr.site on
                        <a href="#" class="text-blue-400 underline hover:text-blue-300">X</a>
                        and
                        <a href="#" class="text-blue-400 underline hover:text-blue-300">Discord</a>
                    </div>

                    <div class="flex items-center gap-2 sm:gap-3">
                        <button
                            @click="theme = 'dark'"
                            type="button"
                            :class="[
                                'cursor-pointer text-xs font-medium transition-all hover:opacity-80',
                                theme === 'dark' ? 'text-white' : theme === 'dark' ? 'text-gray-400' : 'text-gray-500',
                            ]"
                        >
                            Dark
                        </button>
                        <div class="relative h-4 w-8 cursor-pointer rounded-full bg-gray-600" @click="toggleTheme">
                            <div
                                :class="[
                                    'absolute top-0.5 h-3 w-3 rounded-full bg-white transition-transform duration-200',
                                    theme === 'dark' ? 'left-0.5' : 'left-4',
                                ]"
                            ></div>
                        </div>
                        <button
                            @click="theme = 'light'"
                            type="button"
                            :class="[
                                'cursor-pointer text-xs font-medium transition-all hover:opacity-80',
                                theme === 'light'
                                    ? theme === 'dark'
                                        ? 'text-white'
                                        : 'text-gray-900'
                                    : theme === 'dark'
                                      ? 'text-gray-400'
                                      : 'text-gray-500',
                            ]"
                        >
                            Light
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Background Decoration - Responsive positioning -->
        <div
            :class="[
                'pointer-events-none absolute top-1/4 left-1/4 h-48 w-48 rounded-full blur-3xl transition-opacity duration-500 sm:h-64 sm:w-64 lg:h-96 lg:w-96',
                theme === 'dark' ? 'bg-white/5' : 'bg-white/10',
            ]"
        />
        <div
            :class="[
                'pointer-events-none absolute right-1/4 bottom-1/4 h-32 w-32 rounded-full blur-3xl transition-opacity duration-500 sm:h-48 sm:w-48 lg:h-64 lg:w-64',
                theme === 'dark' ? 'bg-white/3' : 'bg-white/5',
            ]"
        />
    </div>
</template>

<script setup lang="ts">
import { ref, type Ref } from 'vue';

type Theme = 'dark' | 'light';
type Tab = 'waitlist' | 'manifesto';

const activeTab: Ref<Tab> = ref('waitlist');
const theme: Ref<Theme> = ref('dark');
const email: Ref<string> = ref('');

// Simple toggle between dark and light
const toggleTheme = (): void => {
    theme.value = theme.value === 'dark' ? 'light' : 'dark';
};

// Join waitlist function
const joinWaitlist = (): void => {
    if (email.value && email.value.trim()) {
        alert(`Thank you! ${email.value} has been added to our waitlist.`);
        email.value = '';
    } else {
        alert('Please enter a valid email address.');
    }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;500;600;700&display=swap');

.font-signature {
    font-family: 'Dancing Script', cursive;
}

/* Additional responsive utilities */
@media (max-width: 640px) {
    .font-signature {
        line-height: 1.2;
    }
}
</style>
