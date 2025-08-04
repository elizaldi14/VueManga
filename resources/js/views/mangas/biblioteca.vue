<script setup>
import CardGrande from "@layouts/components/CardGrandesMangas.vue";
import DropDown from "@layouts/components/DropDown.vue";

const generoOptions = ["Acción", "Magia", "Drama", "Terror"];
const origenOptions = ["Manga", "Manhwa", "Manhua", "Otro"];
const tipoOptions = ["Shounen", "Seinen", "Josei", "Kodomo"];
const estadoOptions = ["En emisión", "Finalizado", "Pausado"];
const ordenOptions = ["Puntuación", "Capítulos", "Popularidad"];

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
</script>

<template>
  <div class="navbar-container">
    <VRow dense>
      <VCol cols="6" sm="4" md="2">
        <DropDown
          label="Género"
          :options="generoOptions"
          @update:selected="(val) => console.log('Género:', val)"
        />
      </VCol>
      <VCol cols="6" sm="4" md="2">
        <DropDown
          label="Origen"
          :options="origenOptions"
          @update:selected="(val) => console.log('Origen:', val)"
        />
      </VCol>
      <VCol cols="6" sm="4" md="2">
        <DropDown
          label="Tipo"
          :options="tipoOptions"
          @update:selected="(val) => console.log('Tipo:', val)"
        />
      </VCol>
      <VCol cols="6" sm="4" md="2">
        <DropDown
          label="Estado"
          :options="estadoOptions"
          @update:selected="(val) => console.log('Estado:', val)"
        />
      </VCol>
      <VCol cols="6" sm="4" md="2">
        <DropDown
          label="Ordenar por"
          :options="ordenOptions"
          @update:selected="(val) => console.log('Orden:', val)"
        />
      </VCol>
      <VCol cols="6" sm="4" md="2" class="d-flex align-center justify-center">
        <VBtn variant="tonal" class="filter-btn" size="large" block>
          Filtrar
        </VBtn>
      </VCol>
    </VRow>
    <!-- </div>

  <div style="margin: 20px"> -->
    <VRow justify="center">
      <VCol :cols="12">
        <VCard class="pa-6" elevation="2">
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

<style lang="scss" scoped>
.navbar-container {
  border-radius: 1rem;
  background-color: rgb(var(--v-theme-surface));
  border-bottom: 1px solid rgba(var(--v-border-color), var(--v-border-opacity));
  padding: 1rem;
  width: 100%;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

// Solo ajustar el contenedor para que los elementos se alineen bien
:deep(.v-col) {
  display: flex !important;
  flex-direction: column !important;
  align-items: stretch !important;
}

.filter-btn {
  // Solo sobrescribir dimensiones y espaciado, mantener colores y efectos de Vuetify
  min-height: 56px !important;
  height: 56px !important;
  border-radius: 12px !important;
  margin-bottom: 12px !important;
  border: 1px solid rgba(var(--v-border-color), var(--v-border-opacity)) !important;

  // NO sobrescribir background, color, border - dejar que Vuetify los maneje
}

/* Responsive - solo ajustar tamaños */
@media (max-width: 768px) {
  .filter-btn {
    height: 60px !important;
    min-height: 60px !important;
  }
}

@media (max-width: 480px) {
  .filter-btn {
    height: 64px !important;
    min-height: 64px !important;
    margin-bottom: 8px !important;
  }
}
</style>
