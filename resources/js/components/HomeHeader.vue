<script setup lang="ts">
import mainLogo from '@/assets/logo/main-logo.png';
import HomeHeaderMenu from '@/components/HomeHeaderMenu.vue';
import HomeHeaderProfile from '@/components/HomeHeaderProfile.vue';
import { index } from '@/wayfinder/routes';
import { index as storiesIndex } from '@/wayfinder/routes/stories';
import { Link } from '@inertiajs/vue3';
</script>

<template>
    <header class="home-header-bar relative z-20 flex min-h-[91px] items-center overflow-visible">
        <div class="relative container w-full overflow-visible py-0">
            <div
                class="container-content grid h-[75px] grid-cols-[auto_1fr_auto] grid-rows-1 items-center gap-x-4 gap-y-3 overflow-visible md:gap-x-[50px] md:gap-y-0"
            >
                <Link
                    :href="index().url"
                    class="logo-link shrink-0 justify-self-start pr-1 ring-offset-2 ring-offset-black outline-none focus-visible:ring-2 focus-visible:ring-[#00C6DE] md:pr-0"
                >
                    <img
                        :src="mainLogo"
                        alt="LoreSpinner"
                        class="brand-logo select-none"
                        width="296"
                        height="58"
                        decoding="async"
                    />
                </Link>

                <div class="hidden min-w-0 items-center justify-center gap-0 justify-self-center md:flex">
                    <HomeHeaderMenu />
                    <Link
                        :href="storiesIndex().url"
                        class="featured-worlds-btn inline-flex h-10 shrink-0 items-center justify-center rounded-full px-5 text-[15px] font-normal whitespace-nowrap"
                    >
                        Featured worlds
                    </Link>
                </div>

                <div class="flex shrink-0 items-center justify-end justify-self-end">
                    <HomeHeaderProfile />
                </div>
            </div>
        </div>
    </header>
</template>

<style scoped>
.home-header-bar {
    background:rgba(0, 0, 0);
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(6px);
    -webkit-backdrop-filter: blur(6px);
}

/*
 * Toolbar row stays 75px (Figma). Logo asset was authored ~45px tall in frame;
 * at that size it looked undersized next to nav (16px type + controls). Use ~58px
 * height (~1.29×) so the lockup matches visual weight; width follows aspect ratio.
 */
.brand-logo {
    display: block;
    width: auto;
    max-width: min(100%, 300px);
    height: clamp(2.25rem, 7.5vw, 3.625rem);
    object-fit: contain;
    object-position: left center;
}

@media (min-width: 768px) {
    .brand-logo {
        height: 58px;
        max-width: min(100%, 300px);
    }
}

.logo-link {
    display: inline-flex;
    align-items: center;
    align-self: center;
}

.featured-worlds-btn {
    background: linear-gradient(180deg, #3a4d52 0%, #2c3b3f 100%);
    color: #c8ced1;
    border: 1px solid rgba(255, 255, 255, 0.08);
    box-shadow:
        0 2px 8px rgba(0, 0, 0, 0.35),
        inset 0 1px 0 rgba(255, 255, 255, 0.06);
    transition:
        color 0.15s ease,
        background 0.15s ease,
        border-color 0.15s ease;
}

.featured-worlds-btn:hover {
    color: #e8ebed;
    background: linear-gradient(180deg, #45595f 0%, #35474c 100%);
    border-color: rgba(0, 198, 222, 0.25);
}

.featured-worlds-btn:focus-visible {
    outline: 2px solid #00c6de;
    outline-offset: 2px;
}
</style>
