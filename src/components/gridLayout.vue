<template>
  <div class="grid-photos">
    <div class="grid-photos__item" v-for="photo in props.photos">
      <img class="grid-photos__image" :src="photo" alt="picture" />
      <div class="grid-photos__image-info image-info">
        <div class="image-info__today today">
          <p class="today__label">Today</p>
          <div class="today__like">
            <svg class="icon-like" width="18" height="18">
              <use href="../assets/icons.svg#icon-like"></use>
            </svg>
            <p class="today__like-number">128</p>
          </div>
          <div class="today__comment">
            <svg class="icon-comment" width="18" height="18">
              <use href="../assets/icons.svg#icon-comment"></use>
            </svg>
            <p class="today__comment-number">31</p>
          </div>
        </div>
        <div class="image-info__other-date other-date">
          <p class="other-date__label">9-08-2016</p>
          <div class="other-date__like">
            <svg class="icon-like" width="18" height="18">
              <use href="../assets/icons.svg#icon-like"></use>
            </svg>
            <p>67</p>
          </div>
          <div class="other-date__comment">
            <svg class="icon-comment" width="18" height="18">
              <use href="../assets/icons.svg#icon-comment"></use>
            </svg>
            <p>22</p>
          </div>
        </div>
      </div>
      <div class="grid-photos__upload-date upload-date">
        <p class="upload-date__label">Image upload</p>
        <p class="upload-date__date">11-04-2016</p>
      </div>
    </div>
  </div>
  <button class="load-more-button" type="button">load more</button>
</template>

<script setup>
const props = defineProps({
  photos: {
    type: Array,
    required: true,
  },
});
</script>
