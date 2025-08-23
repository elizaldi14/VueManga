<script setup>
defineProps({
  title: String,
  genre: String,
  type: String,
  rating: Number,
  image: String,
});
</script>
<template>
  <VCard class="card-large">
    <a href="#">
      <img :src="image" alt="Portada" class="card-img" loading="lazy" />
      <div class="card-overlay"></div>
      <div class="tag-type">{{ type }}</div>
      <div class="rating-stars">
        <span> ★ {{ rating }} </span>
      </div>
      <div class="tag-genre">{{ genre }}</div>
      <div class="tag-title" :title="title">{{ title }}</div>
    </a>
  </VCard>
</template>

<style scoped>
.card-large {
  position: relative;
  width: 100%;
  display: inline-block;
  overflow: hidden;
  border-radius: 12px;
  background-color: rgb(var(--v-theme-background));
}

.card-img {
  width: 100%;
  height: auto; /* La imagen define el alto */
  object-fit: contain; /* Se asegura de que se vea completa */
  display: block;
  transition: opacity 0.3s ease;
}

.card-large:hover .card-img {
  opacity: 0.6;
}

/* Overlay y etiquetas */
.card-overlay,
.tag-type,
.rating-stars,
.tag-genre,
.tag-title {
  position: absolute;
  z-index: 2;
}

.card-overlay {
  top: 0;
  left: 0;
  right: 0;
  height: 10px;
  box-shadow: 0 -4px 12px rgba(0, 0, 0, 0.1), -4px 0 12px rgba(0, 0, 0, 0.05),
    4px 0 12px rgba(0, 0, 0, 0.05);
}

.tag-type {
  top: 8px;
  left: 8px;
  background: rgba(37, 138, 233, 0.8);
  color: white;
  font-size: 0.65rem;
  padding: 0.2rem 0.4rem;
  border-radius: 6px;
  font-size: 1.1rem;
}

.rating-stars {
  top: 8px;
  right: 8px;
  background: rgba(0, 0, 0, 0.7);
  color: gold;
  font-weight: bold;
  font-size: 0.75rem;
  padding: 0.1rem 0.3rem;
  border-radius: 6px;
}

.tag-genre {
  bottom: 2.2rem;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(232, 38, 38, 0.7);
  color: white;
  font-size: 0.7rem;
  padding: 0.25rem 1rem;
  border-radius: 6px;
}

.tag-title {
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.7);
  color: white;
  text-align: center;
  padding: 0.25rem 0.4rem;
  font-size: 0.85rem;
  font-weight: 600;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  border-radius: 0 0 6px 6px;
}
</style>
