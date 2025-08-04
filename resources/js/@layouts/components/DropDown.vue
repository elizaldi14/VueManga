<!-- MultiSelectDropdown.vue -->
<script setup>
import { onBeforeUnmount, onMounted, ref, watch } from "vue";

const props = defineProps({
  label: {
    type: String,
    default: "Género",
  },
  options: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["update:selected"]);

const selected = ref([]);
const show = ref(false);
const dropdown = ref(null);

function toggleDropdown() {
  show.value = !show.value;
}

function handleClickOutside(event) {
  if (dropdown.value && !dropdown.value.contains(event.target)) {
    show.value = false;
  }
}

// Cerrar dropdown cuando se abra otro (usando evento personalizado)
function handleGlobalDropdownOpen() {
  show.value = false;
}

watch(selected, (val) => {
  emit("update:selected", val);
});

// Watch para emitir evento cuando se abre este dropdown
watch(show, (newVal) => {
  if (newVal) {
    // Emitir evento global para cerrar otros dropdowns
    document.dispatchEvent(
      new CustomEvent("dropdown-opened", {
        detail: { source: dropdown.value },
      })
    );
  }
});

onMounted(() => {
  document.addEventListener("click", handleClickOutside);
  document.addEventListener("dropdown-opened", (event) => {
    // Solo cerrar si el evento no viene de este dropdown
    if (event.detail.source !== dropdown.value) {
      show.value = false;
    }
  });
});

onBeforeUnmount(() => {
  document.removeEventListener("click", handleClickOutside);
  document.removeEventListener("dropdown-opened", handleGlobalDropdownOpen);
});
</script>

<template>
  <div class="dropdown" ref="dropdown">
    <button class="dropdown-btn" @click.stop="toggleDropdown">
      <span class="dropdown-text">
        {{ label }}:
        <span class="selected-count">
          {{
            selected.length
              ? selected.length === 1
                ? selected[0]
                : `${selected.length} Seleccionados`
              : "Todos"
          }}
        </span>
      </span>
      <VIcon
        icon="bx-chevron-down"
        class="nav-item-icon"
        :class="{ rotated: show }"
      />
    </button>

    <transition name="zoom">
      <div v-if="show" class="dropdown-menu" color="primary">
        <label v-for="option in options" :key="option" class="dropdown-item">
          <input type="checkbox" :value="option" v-model="selected" />
          <span class="option-text">{{ option }}</span>
        </label>
      </div>
    </transition>
  </div>
</template>

<style scoped>
.dropdown {
  position: relative;
  display: block;
  width: 100%;
  margin-bottom: 12px;
}

.dropdown-btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  padding: 10px 14px;
  border: 1px solid rgba(var(--v-theme-secondary));
  border-radius: 12px;
  cursor: pointer;
  /* background: white; */
  width: 100%;
  min-height: 44px; /* Altura mínima para evitar colapso */
  font-size: 14px;
  transition: border-color 0.2s ease;
}

/* .dropdown-btn:hover {
  border-color: #999;
} */

.dropdown-btn:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 0 2px rgba(0, 123, 255, 0.25);
}

.dropdown-text {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex: 1;
  min-width: 0; /* Permite que el texto se contraiga */
  gap: 2px;
}

.selected-count {
  font-size: 12px;
  /* color: #666; */
  font-weight: normal;
}

.dropdown-menu {
  position: absolute;
  top: calc(100% + 4px);
  left: 0;
  right: 0;
  z-index: 1000; /* Z-index alto para estar por encima de otros elementos */
  background-color: rgba(var(--v-theme-surface));
  opacity: 0.9;
  border: 1px solid rgba(var(--v-theme-primary-darken-1));
  padding: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  border-radius: 8px;
  max-height: 200px; /* Altura máxima con scroll */
  overflow-y: auto;
}

.dropdown-item {
  display: flex;
  align-items: center;
  padding: 6px 4px;
  margin-bottom: 4px;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.2s ease;
}

.dropdown-item:hover {
  /* background-color: #f5f5f5; */
}

.dropdown-item:last-child {
  margin-bottom: 0;
}

.dropdown-item input {
  margin-right: 8px;
  cursor: pointer;
}

.option-text {
  flex: 1;
  font-size: 14px;
}

.nav-item-icon {
  font-size: 18px;
  transition: transform 0.2s ease;
  flex-shrink: 0; /* No se contraiga */
}

.nav-item-icon.rotated {
  transform: rotate(180deg);
}

/* Animaciones */
.zoom-enter-active,
.zoom-leave-active {
  transition: all 0.2s ease;
  transform-origin: top center;
}

.zoom-enter-from,
.zoom-leave-to {
  transform: scaleY(0.8);
  opacity: 0;
}

.zoom-enter-to,
.zoom-leave-from {
  transform: scaleY(1);
  opacity: 1;
}

/* Responsive */
@media (max-width: 768px) {
  .dropdown-btn {
    padding: 12px 16px;
    min-height: 48px;
    font-size: 16px; /* Tamaño mínimo para iOS */
  }

  .dropdown-text {
    gap: 4px;
  }

  .selected-count {
    font-size: 13px;
  }

  .dropdown-menu {
    max-height: 250px;
    padding: 12px;
  }

  .dropdown-item {
    padding: 10px 8px;
    margin-bottom: 8px;
  }

  .option-text {
    font-size: 16px;
  }
}

@media (max-width: 480px) {
  .dropdown {
    margin-bottom: 8px;
  }

  .dropdown-btn {
    padding: 14px 16px;
    min-height: 52px;
  }

  .dropdown-menu {
    left: -4px;
    right: -4px;
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
  }
}
</style>
