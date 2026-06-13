<template>
  <div class="order-photos">
    <div class="order-photos__item" v-for="photo in props.photos">
      <div class="order-photos__today order-today">
        <img class="order-photos__image" :src="photo" alt="image" />
        <div class="order-today__container">
          <p class="order-today__text">Today</p>
          <div class="order-today__statistic">
            <div class="order-today__like">
              <svg class="icon-like" width="18" height="18">
                <use href="../assets/icons.svg#icon-like"></use>
              </svg>
              <p class="order-today__like-number">128</p>
            </div>
            <div class="order-today__comment">
              <svg class="icon-comment" width="18" height="18">
                <use href="../assets/icons.svg#icon-comment"></use>
              </svg>
              <p class="order-today__comment-number">31</p>
            </div>
          </div>
        </div>
      </div>
      <div class="order-photos__other-day order-other-day">
        <div class="order-other-day__container">
          <p class="order-other-day__text">9-08-2016</p>
          <div class="order-other-day__statistic">
            <div class="order-other-day__like">
              <svg class="icon-like" width="18" height="18">
                <use href="../assets/icons.svg#icon-like"></use>
              </svg>
              <p class="order-other-day__like-number">67</p>
            </div>
            <div class="order-other-day__comment">
              <svg class="icon-comment" width="18" height="18">
                <use href="../assets/icons.svg#icon-comment"></use>
              </svg>
              <p class="order-other-day__comment-number">22</p>
            </div>
          </div>
        </div>
      </div>
      <div class="order-photos__upload-date order-upload-date">
        <p class="order-upload-date__label">Image upload</p>
        <p class="order-upload-date__date">11-04-2016</p>
      </div>
    </div>
    <button class="load-more-button" type="button">load more</button>
  </div>
</template>

<script setup>
const props = defineProps({
  photos: {
    type: Array,
    required: true,
  },
});
</script>
