<template>
  <div class="font-poppins antialiased">
    <div id="view" class="h-full w-screen flex flex-row">
      <AppSidebar/>
      <div class="mx-auto w-96 mt-12">
        <slot/>
      </div>
    </div>
  </div>
</template>