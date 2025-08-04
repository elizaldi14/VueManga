<script setup>
import UserProfile from "@/layouts/components/UserProfile.vue";
import Footer from "@layouts/components/Footer.vue";
import TopMenu from "@layouts/components/TopMenu.vue";
import { computed } from "vue";
import { useDisplay } from "vuetify";

// Mostrar/Ocultar navbar según scroll
const display = useDisplay();
const isMobile = computed(() => display.smAndDown.value);
const isTablet = computed(() => display.md.value);
const isPc = computed(() => display.lgAndUp.value);

// Rutas para el menú inferior
const statuses = [
  { label: "Inicio", icon: "bx-home", route: "/home" },
  { label: "Biblioteca", icon: "bx-book", route: "/library" },
  { label: "Grupos", icon: "bx-group", route: "/groups" },
  { label: "Lista", icon: "bx-list-ul", route: "/list" },
];
</script>

<template>
  <div class="main-layout">
    <TopMenu />

    <VContainer class="layout-content" fluid>
      <RouterView />
    </VContainer>

    <!-- Footer solo en PC -->
    <VContainer class="footer-container" fluid v-if="isPc">
      <Footer />
    </VContainer>

    <!-- Navbar móvil solo en tablets y móviles -->
    <div v-if="isMobile || isTablet" class="mobile-navbar">
      <div class="navbar-container">
        <div class="status-bar d-flex justify-space-around align-center">
          <router-link
            v-for="status in statuses"
            :key="status.label"
            :to="status.route"
            class="text-button mb-0 cursor-pointer menuOption"
          >
            <div class="status-item d-flex flex-column align-center">
              <VIcon :icon="status.icon" size="24" />
              <span class="status-label">{{ status.label }}</span>
            </div>
          </router-link>

          <!-- UserProfile al final -->
          <router-link
            to="/profile"
            class="text-button mb-0 cursor-pointer menuOption"
          >
            <div class="d-flex flex-column align-center">
              <UserProfile />
              <span class="status-label">Perfil</span>
            </div>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.layout-content {
  flex: 1;
  padding-top: 16px;
  padding-bottom: 60px; /* espacio para que no lo tape el navbar */
}

/* Navbar móvil fija abajo */
.mobile-navbar {
  position: fixed;
  bottom: 0;
  width: 100%;
  z-index: 1000;
  transform: translateY(0);
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  background-color: rgb(var(--v-theme-surface));
}

/* Ocultar navbar con transición */
.navbar-hidden {
  transform: translateY(100%);
}

.status-bar {
  width: 100%;
  gap: 16px;
}

.status-bar > * {
  flex: 1;
  min-width: 0;
  text-align: center;
}

.status-item {
  padding-bottom: 4px;
  color: rgba(var(--v-theme-on-surface), 0.87);
}

.status-label {
  font-size: 0.75rem;
  font-weight: 500;
  margin-top: 4px;
}

.navbar-container {
  border-top: 1px solid rgba(var(--v-border-color), var(--v-border-opacity));
  padding: 0.75rem 1rem;
  box-shadow: 0 -1px 4px rgba(0, 0, 0, 0.05);
}

@media (hover: hover) {
  .mobile-navbar {
    transition: transform 0.25s ease-out;
  }
}
</style>
