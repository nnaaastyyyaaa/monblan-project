<template>
  <div class="app-main">
    <svg class="icon-top" width="625" height="482">
      <use xlink:href="/icons.svg#icon-top">></use>
    </svg>
    <svg class="icon-bottom" width="314" height="368">
      <use xlink:href="/icons.svg#icon-bottom"></use>
    </svg>
    <div class="header">
      <svg class="icon-logo" width="138" height="138">
        <use xlink:href="/icons.svg#icon-logo"></use>
      </svg>
      <div class="header__text-container text-container">
        <div class="text-container__block">
          <h1 class="text-container__title">Monblanproject</h1>
          <p class="text-container__text">Start on 17-02-2016</p>
        </div>
        <div class="text-container__block">
          <p class="text-container__account-info">
            <span class="text-container__account-info--accent">870</span> posts
          </p>
          <p class="text-container__account-info">
            <span class="text-container__account-info--accent">11,787</span>
            followers
          </p>
          <p class="text-container__account-info">
            <span class="text-container__account-info--accent">112</span>
            following
          </p>
        </div>
        <div class="text-container__block">
          <p class="text-container__filter-label">Date</p>
          <div
            class="text-container__custom-calendar-input custom-calendar-input"
          >
            <div class="custom-calendar-input__input-field input-field">
              <input
                :value="dateFrom"
                class="input-field__input"
                type="text"
                placeholder="from"
                disabled
              />
            </div>
            <div
              class="custom-calendar-input__close-calendar"
              @click="removeDate('from')"
            >
              <svg class="icon-close" width="24" height="24">
                <use xlink:href="/icons.svg#icon-close"></use>
              </svg>
            </div>
            <div class="custom-calendar-input__input-date">
              <FlatPickr
                v-model="dateFrom"
                :config="config"
                class="datepicker"
              />
              <svg class="icon-calendar" width="24" height="24">
                <use xlink:href="/icons.svg#icon-calendar"></use>
              </svg>
            </div>
          </div>
          <div
            class="text-container__custom-calendar-input custom-calendar-input"
          >
            <div class="custom-calendar-input__input-field input-field">
              <input
                :value="dateTo"
                class="input-field__input"
                type="text"
                placeholder="to"
                disabled
              />
            </div>
            <div
              class="custom-calendar-input__close-calendar"
              @click="removeDate('to')"
            >
              <svg class="icon-close" width="24" height="24">
                <use xlink:href="/icons.svg#icon-close"></use>
              </svg>
            </div>
            <div class="custom-calendar-input__input-date">
              <FlatPickr v-model="dateTo" :config="config" class="datepicker" />
              <svg class="icon-calendar" width="24" height="24">
                <use xlink:href="/icons.svg#icon-calendar"></use>
              </svg>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="main-content">
      <div class="content-position-btns">
        <svg
          class="icon-grid"
          :class="{ active: currentComponent === 'grid' }"
          width="24"
          height="24"
          @click="changeLayout('grid')"
        >
          <use xlink:href="/icons.svg#icon-grid"></use>
        </svg>
        <svg
          class="icon-order"
          :class="{ active: currentComponent === 'order' }"
          width="24"
          height="24"
          @click="changeLayout('order')"
        >
          <use xlink:href="/icons.svg#icon-order"></use>
        </svg>
      </div>
      <component :is="layouts[currentComponent + 'Layout']" :photos="photos" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import FlatPickr from "vue-flatpickr-component";
import "flatpickr/dist/flatpickr.css";
import flatpickr from "flatpickr";
import iconsUrl from "/icons.svg";
import gridLayout from "./gridLayout.vue";
import orderLayout from "./orderLayout.vue";

const dateFrom = ref(null);
const dateTo = ref(null);

const currentComponent = ref("grid");

const config = {
  dateFormat: "d_m_Y",
  allowInput: true,
  prevArrow: `<svg class="icon-prev" width="24" height="24">
                <use href="${iconsUrl}#icon-prev"></use>
              </svg>`,
  nextArrow: `<svg class="icon-next" width="24" height="24">
                <use href="${iconsUrl}#icon-next"></use>
              </svg>`,
  monthSelectorType: "static",
  yearSelectorType: "static",

  locale: {
    weekdays: {
      shorthand: ["Su", "Mo", "Tu", "We", "Th", "Fr", "Sa"],
      longhand: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ],
    },
  },
};

const layouts = {
  gridLayout,
  orderLayout,
};

const photos = [
  "./images/Rectangle20.png",
  "./images/Rectangle21.png",
  "./images/Rectangle22.png",
  "./images/Rectangle23.png",
  "./images/Rectangle24.png",
  "./images/Rectangle25.png",
  "./images/Rectangle26.png",
  "./images/Rectangle27.png",
];

const removeDate = (type) => {
  type === "from" ? (dateFrom.value = null) : (dateTo.value = null);
};

const changeLayout = (layout) => {
  currentComponent.value = layout;
};
</script>
