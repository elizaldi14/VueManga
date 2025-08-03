<template>
  <div
    class="h-100 d-flex align-center justify-md-space-between justify-center"
  >
    <!-- 👉 Footer: left content -->
    <span class="d-flex align-items-center">
      &copy; {{ new Date().getFullYear() }} Made With
      <span style="color: #f44336; font-weight: bold" class="mx-1"> 平和 </span>
      By
      <a
        href="https://themeselection.com"
        target="_blank"
        rel="noopener noreferrer"
        class="text-primary ms-1"
      >
        Erert
      </a>
    </span>

    <!-- 👉 Footer: right content -->
    <span class="d-md-flex gap-x-4 text-primary d-none">
      <a href="https://themeselection.com/license/" target="noopener noreferrer"
        >Sobre VueManga</a
      >
      <a href="https://themeselection.com/" target="noopener noreferrer"
        >Desarrolladores</a
      >
      <a
        href="https://demos.themeselection.com/sneat-vuetify-vuejs-admin-template/documentation/guide/laravel-integration/folder-structure.html"
        target="noopener noreferrer"
        >Peticiones</a
      >
      <a href="https://themeselection.com/support/" target="noopener noreferrer"
        >Soporte</a
      >
    </span>
  </div>
</template>
