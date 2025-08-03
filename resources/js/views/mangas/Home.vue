<script setup>
import CardGrande from "@layouts/components/CardGrandesMangas.vue";
import Card from "@layouts/components/CardManga.vue";
import TopMangas from "@layouts/components/TopMangas.vue";
import { useDisplay } from "vuetify";

// Detectar si estamos en escritorio
const { mdAndUp } = useDisplay();
const isDesktop = mdAndUp;
const route = useRoute();
const activeTab = ref(route.params.tab);

const mangas = [
  {
    title: "Kusuriya no Hitorigoto",
    genre: "Seinen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/e0/44dc907afa5d2d8ee792485763063e.jpg?v1742834285442",
  },
  {
    title: "One Piece",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/70/0497d3d55cca5809e2c025775d751d.jpg?v1742834285442",
  },
  {
    title: "Attack on Titan",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/58/d98d7af95103c084517686908dbf46.jpg?v1742834285442",
  },
  {
    title: "Death Note",
    genre: "Mystery",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/73/821bbe3312dd35cd29a55f6427151e.jpg?v1742834285442",
  },
  {
    title: "Tokyo Ghoul",
    genre: "Seinen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/7b/c5e9690e84cc6d354b905467ab1f3b.jpg?v1742834285442",
  },
  {
    title: "Demon Slayer",
    genre: "Shounen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/c2/d48eee70f787d4566aa6b349421a7f.jpg?v1742834285442",
  },
  {
    title: "Naruto",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/21/0eb763360d2a51c6e486d5b1bfada2.jpg?v1742834285442",
  },
  {
    title: "Bleach",
    genre: "Shounen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/4b/5a64067d33747c32c4a2ed611159a7.jpg?v1742834285442",
  },
  {
    title: "Chainsaw Man",
    genre: "Action",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/7d/c29ca693f37cfe0331f713095586ff.jpg?v1742834285442",
  },
  {
    title: "Jujutsu Kaisen",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/a8/323b30490822127cd9232558359cdf.jpg?v1742834285442",
  },
  {
    title: "Vagabond",
    genre: "Seinen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/aa/acdf576a44adcd97718820cc0a423d.jpg?v1742834285442",
  },
  {
    title: "Spy x Family",
    genre: "Comedy",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/54/5e5a5ed27880e8e48354e0e49f1a02.jpg?v1742834285442",
  },
];
const grande = [
  {
    title: "Kusuriya no Hitorigoto",
    genre: "Seinen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/e0/44dc907afa5d2d8ee792485763063e.jpg?v1742834285442",
  },
  {
    title: "One Piece",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/70/0497d3d55cca5809e2c025775d751d.jpg?v1742834285442",
  },
  {
    title: "Attack on Titan",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/58/d98d7af95103c084517686908dbf46.jpg?v1742834285442",
  },
  {
    title: "Death Note",
    genre: "Mystery",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/73/821bbe3312dd35cd29a55f6427151e.jpg?v1742834285442",
  },
  {
    title: "Tokyo Ghoul",
    genre: "Seinen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/7b/c5e9690e84cc6d354b905467ab1f3b.jpg?v1742834285442",
  },
  {
    title: "Demon Slayer",
    genre: "Shounen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/c2/d48eee70f787d4566aa6b349421a7f.jpg?v1742834285442",
  },
  {
    title: "Naruto",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/21/0eb763360d2a51c6e486d5b1bfada2.jpg?v1742834285442",
  },
  {
    title: "Bleach",
    genre: "Shounen",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/4b/5a64067d33747c32c4a2ed611159a7.jpg?v1742834285442",
  },
  {
    title: "Chainsaw Man",
    genre: "Action",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/7d/c29ca693f37cfe0331f713095586ff.jpg?v1742834285442",
  },
  {
    title: "Jujutsu Kaisen",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/a8/323b30490822127cd9232558359cdf.jpg?v1742834285442",
  },
  {
    title: "Vagabond",
    genre: "Seinen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/aa/acdf576a44adcd97718820cc0a423d.jpg?v1742834285442",
  },
  {
    title: "Spy x Family",
    genre: "Comedy",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/54/5e5a5ed27880e8e48354e0e49f1a02.jpg?v1742834285442",
  },
  {
    title: "Jujutsu Kaisen",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/a8/323b30490822127cd9232558359cdf.jpg?v1742834285442",
  },
  {
    title: "Vagabond",
    genre: "Seinen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/aa/acdf576a44adcd97718820cc0a423d.jpg?v1742834285442",
  },
  {
    title: "Spy x Family",
    genre: "Comedy",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/54/5e5a5ed27880e8e48354e0e49f1a02.jpg?v1742834285442",
  },
  {
    title: "Jujutsu Kaisen",
    genre: "Shounen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/a8/323b30490822127cd9232558359cdf.jpg?v1742834285442",
  },
  {
    title: "Vagabond",
    genre: "Seinen",
    type: "Manga",
    rating: 5,
    image:
      "https://www.leercapitulo.co/covers/aa/acdf576a44adcd97718820cc0a423d.jpg?v1742834285442",
  },
  {
    title: "Spy x Family",
    genre: "Comedy",
    type: "Manga",
    rating: 4,
    image:
      "https://www.leercapitulo.co/covers/54/5e5a5ed27880e8e48354e0e49f1a02.jpg?v1742834285442",
  },
];

const tabs = [
  {
    title: "Populares",
    icon: "bxs-star",
    tab: "account",
  },
  {
    title: "P.Seinen",
    icon: "bxs-heart",
    tab: "security",
  },
  {
    title: "P.Josei",
    icon: "bxs-heart",
    tab: "notification",
  },
];

const statuses = [
  { label: "Leído", icon: "bxs-book", color: "#4CAF50" },
  { label: "Pendiente", icon: "bxs-time", color: "#FF9800" },
  { label: "Siguiendo", icon: "bxs-show", color: "#2196F3" },
  { label: "Favorito", icon: "bxs-heart", color: "#E91E63" },
  { label: "Lo tengo", icon: "bxs-bookmark", color: "#9C27B0" },
  { label: "Abandonado", icon: "bxs-x-circle", color: "#F44336" },
];
</script>
<template>
  <!-- <VRow>
    <VCol cols="12">
      <TopMenu />
    </VCol>
  </VRow> -->

  <!-- Cards Pequeñas -->
  <div style="margin: 20px">
    <VRow justify="center">
      <VCol :cols="12" :sm="isDesktop ? 9 : 12">
        <VCard class="pa-6" elevation="2">
          <div>
            <div class="d-flex justify-center">
              <VTabs
                v-model="activeTab"
                show-arrows
                class="v-tabs-pill full-width-tabs"
                height="32"
              >
                <VTab
                  v-for="item in tabs"
                  :key="item.icon"
                  :value="item.tab"
                  class="tab-item"
                >
                  <VIcon size="24" start :icon="item.icon" />
                  {{ item.title }}
                </VTab>
              </VTabs>
            </div>

            <VRow justify="center" class="mt-4">
              <VCol
                v-for="(manga, index) in mangas"
                :key="index"
                cols="6"
                sm="4"
                md="2"
                class="d-flex justify-center"
              >
                <Card
                  :title="manga.title"
                  :genre="manga.genre"
                  :type="manga.type"
                  :rating="manga.rating"
                  :image="manga.image"
                />
              </VCol>
            </VRow>
          </div>
        </VCard>
      </VCol>

      <VCol cols="12" sm="3" v-if="isDesktop">
        <TopMangas />
        <br />
      </VCol>
    </VRow>
  </div>

  <div class="navbar-container px-4 py-2">
    <VRow class="status-icons-row" justify="center">
      <VCol
        v-for="status in statuses"
        :key="status.label"
        cols="4"
        sm="4"
        md="2"
        class="status-item d-flex flex-column align-center"
        :style="{
          '--hover-color': status.color,
          '--item-color': status.color,
        }"
        :title="status.label"
      >
        <i :class="status.icon" class="status-icon" />
        <span class="status-label">{{ status.label }}</span>
      </VCol>
    </VRow>
  </div>

  <div style="margin: 20px">
    <VRow justify="center">
      <VCol :cols="12">
        <VCard class="pa-6" elevation="2">
          <h1 style="text-align: center">Agregado Recientemente</h1>
          <VRow justify="center" class="mt-4">
            <VCol
              v-for="(item, index) in grande"
              :key="index"
              cols="6"
              sm="4"
              md="2"
              class="d-flex justify-center"
            >
              <CardGrande
                :title="item.title"
                :genre="item.genre"
                :type="item.type"
                :rating="item.rating"
                :image="item.image"
              />
            </VCol>
          </VRow>
        </VCard>
      </VCol>
    </VRow>
  </div>
</template>

<style scoped>
.full-width-tabs {
  width: 100%;
  justify-content: space-evenly;
}

.tab-item {
  width: 30%;
  text-align: center;
  padding: 2px 12px;
  font-size: 1rem;
  font-weight: 700;
  min-width: 100px;
}

.navbar-container {
  border-radius: 1rem;
  background-color: rgb(var(--v-theme-surface));
  border-bottom: 1px solid rgba(var(--v-border-color), var(--v-border-opacity));
  padding: 0.5rem 1.5rem;
  /* width: 100%; */
  margin: 1rem;
  /* height: 80px; */
  /* position: sticky; */
  top: 0;
  z-index: 1000;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.status-item {
  position: relative;
  padding-bottom: 8px;
  cursor: pointer;
  transition: transform 0.3s ease;
  color: var(--item-color); /* Aplica color a todo el contenido */
}

.status-item:hover {
  transform: scale(1.1);
}

.status-icon {
  font-size: 24px;
  margin-bottom: 0.25rem;
  transition: transform 0.3s ease;
}

.status-item:hover .status-icon {
  transform: scale(1.2);
}

.status-item::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 25%;
  width: 50%;
  height: 4px;
  background-color: transparent;
  border-radius: 2px;
  transition: background-color 0.3s ease;
}

.status-item:hover::after {
  background-color: var(--hover-color);
}

.status-label {
  font-size: 0.75rem;
  font-weight: 500;
}
</style>
