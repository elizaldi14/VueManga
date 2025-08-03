<script setup>
const transactions = [
  {
    title: "Kusuriya no Hitorigoto",
    top: 1,
    type: "Manga",
    image:
      "https://www.leercapitulo.co/covers/e0/44dc907afa5d2d8ee792485763063e.jpg?v1742834285442",
    color: "error",
  },
  {
    title: "One Piece",
    top: 2,
    type: "Manga",
    image:
      "https://www.leercapitulo.co/covers/70/0497d3d55cca5809e2c025775d751d.jpg?v1742834285442",
    color: "primary",
  },
  {
    top: 3,
    title: "Bleach",
    type: "Manga",
    image:
      "https://www.leercapitulo.co/covers/4b/5a64067d33747c32c4a2ed611159a7.jpg?v1742834285442",
    color: "info",
  },
  {
    title: "Attack on Titan",
    top: 4,
    type: "Manga",
    image:
      "https://www.leercapitulo.co/covers/58/d98d7af95103c084517686908dbf46.jpg?v1742834285442",
    color: "success",
  },
  {
    title: "Death Note",
    top: 5,
    type: "Manga",
    image:
      "https://www.leercapitulo.co/covers/73/821bbe3312dd35cd29a55f6427151e.jpg?v1742834285442",
    color: "primary",
  },
];
</script>

<template>
  <VCard title="TOP SEMANAL">
    <VCardText>
      <VList class="card-list">
        <VListItem
          v-for="item in transactions"
          :key="item.title"
          :href="'/ruta/' + item.title"
          link
        >
          <template #prepend>
            <VAvatar
              rounded
              variant="tonal"
              :color="item.color"
              :image="item.image"
              size="40"
            />
          </template>

          <VListItemTitle class="letras-color">
            {{ item.title }}
          </VListItemTitle>
          <VListItemSubtitle class="letras-color">
            <span id="type-serie">{{ item.type }}</span>
          </VListItemSubtitle>

          <template #append>
            <VListItemAction>
              <span class="me-2">{{ item.top }}</span>
              <span class="text-disabled">#</span>
            </VListItemAction>
          </template>
        </VListItem>
      </VList>
    </VCardText>
  </VCard>
</template>

<style lang="scss" scoped>
.card-list {
  --v-card-list-gap: 1.5rem;
}

.card-list .v-list-item:hover .letras-color {
  color: rgba(var(--v-theme-primary-darken-1));
  cursor: pointer;
}

#type-serie {
  background-color: rgba(37, 138, 233, 0.8);
  color: #fff;
  font-size: clamp(0.6rem, 1vw, 0.8rem);
  padding: 0.1rem 0.4rem;
  border-radius: 6px;
}
</style>
