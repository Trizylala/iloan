<template>
  <div
    class="
      min-h-screen
      flex flex-col
      justify-center
      items-center
      pt-6
      sm:pt-0
      bg-gray-100
      px-[5%]
    "
  >
    <div class="text-center absolute top-0">
      <h1 class="text-3xl font-semibold text-gray-600">NIMROD</h1>
    </div>

    <div
      class="
        w-full
        sm:max-w-md
        mt-6
        pb-10
        px-6
        pt-10
        h-full
        bg-white
        shadow-md
        overflow-hidden
        rounded-lg
      "
    >
      <slot />
    </div>
  </div>
</template>
