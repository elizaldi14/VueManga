<template>
  <div class="navbar-container d-flex align-center justify-between px-4 py-2">
    <!-- Menú móvil -->
    <IconBtn class="d-lg-none" @click="toggleVerticalOverlayNavActive(true)">
      <VIcon icon="bx-menu" />
    </IconBtn>

    <!-- Logo -->
    <img
      src="@images/icons/logo/LogoV2.png"
      alt="Logo"
      style="width: 100px; height: auto"
    />

    <!-- Buscador -->
    <VTextField
      id="searchInput"
      v-model="searchInput"
      prepend-inner-icon="bx-search"
      placeholder="Buscar"
      class="mx-4"
      style="max-width: 300px; border-radius: 2rem"
    />

    <!-- Opciones principales -->
    <div class="d-none d-md-flex gap-4" style="margin-left: 1rem">
      <router-link
        to="/home"
        class="text-button mb-0 cursor-pointer menuOption"
      >
        Inicio
      </router-link>
      <router-link
        to="/library"
        class="text-button mb-0 cursor-pointer menuOption"
      >
        Biblioteca
      </router-link>
      <router-link
        to="/library"
        class="text-button mb-0 cursor-pointer menuOption"
      >
        Grupos
      </router-link>
      <router-link
        to="/library"
        class="text-button mb-0 cursor-pointer menuOption"
      >
        Listas
      </router-link>
    </div>

    <VSpacer />

    <!-- Notificaciones, tema y perfil -->
    <div class="d-flex align-center gap-2">
      <IconBtn><VIcon icon="bx-bell" /></IconBtn>
      <NavbarThemeSwitcher />
      <UserProfile />
    </div>
  </div>
</template>

<script setup>
// Import necessary components
import NavbarThemeSwitcher from "@/layouts/components/NavbarThemeSwitcher.vue";
import UserProfile from "@/layouts/components/UserProfile.vue";
import { ref } from "vue";

const searchInput = ref("");
// Define props if needed
const props = defineProps({
  toggleVerticalOverlayNavActive: {
    type: Function,
    default: () => {},
  },
});
</script>

<style scoped>
.navbar-container {
  border-radius: 1rem;
  background-color: rgb(var(--v-theme-surface));
  border-bottom: 1px solid rgba(var(--v-border-color), var(--v-border-opacity));
  padding: 0.5rem 1.5rem;
  /* width: 100%; */
  margin: 1rem;
  height: 80px;
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.meta-key {
  border: thin solid rgba(var(--v-border-color), var(--v-border-opacity));
  border-radius: 6px;
  font-size: 0.75rem;
  line-height: 1.25rem;
  padding-block: 0.15625rem;
  padding-inline: 0.25rem;
}

/* Estilos para los botones de la barra de navegación */
:deep(.v-btn) {
  color: rgba(var(--v-theme-on-surface), var(--v-high-emphasis-opacity));
}

:deep(.v-btn:hover) {
  background-color: rgba(var(--v-theme-on-surface), 0.04);
}

.menuOption {
  margin-left: 2rem;
  padding: 1rem;
  border-radius: 2rem;
  font-weight: bold;
}

.menuOption:hover {
  background-color: rgba(var(--v-theme-background));
  color: rgba(var(--v-theme-primary-darken-1));
}
</style>
