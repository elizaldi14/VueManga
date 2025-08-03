<!-- MultiSelectDropdown.vue -->
<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";

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

watch(selected, (val) => {
  emit("update:selected", val);
});

onMounted(() => {
  document.addEventListener("click", handleClickOutside);
});

onBeforeUnmount(() => {
  document.removeEventListener("click", handleClickOutside);
});

const option = ["Manga", "anime", "pelicula"];
</script>

<template>
  <div class="dropdown" ref="dropdown">
    <button class="dropdown-btn" @click.stop="toggleDropdown">
      {{ label }}:
      {{ selected.length ? `${selected.length} Seleccionados` : "Todos" }} ▼
    </button>

    <div v-if="show" class="dropdown-menu">
      <label v-for="option in options" :key="option" class="dropdown-item">
        <input type="checkbox" :value="option" v-model="selected" />
        {{ option }}
      </label>
    </div>
  </div>
</template>

<style scoped>
.dropdown {
  position: relative;
  width: 250px;
  height: auto;
  border-radius: 12px;
  background-color: white;
}
.dropdown-btn {
  width: 100%;
  padding: 10px;
  text-align: left;
  border: 1px solid #ccc;
  border-radius: 12px;
  cursor: pointer;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 10;
  background: white;
  border: 1px solid #ccc;
  width: 100%;
  padding: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.15);
}
.dropdown-item {
  display: flex;
  align-items: center;
  margin-bottom: 6px;
}
.dropdown-item input {
  margin-right: 8px;
}
</style>
