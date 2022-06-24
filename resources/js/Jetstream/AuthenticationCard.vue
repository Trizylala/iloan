<template>
    <div class="min-h-screen flex flex-col justify-center items-center pt-6 sm:pt-0 bg-gray-100 px-[5%]">
        <div>
            <slot name="logo" />
        </div>

        <div class="w-full sm:max-w-md mt-6 px-6 pt-10 h-[330px] bg-white shadow-md overflow-hidden rounded-lg">
            <slot />
        </div>
    </div>
</template>
