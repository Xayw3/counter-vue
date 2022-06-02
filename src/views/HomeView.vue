<template>
  <div class="services-wrapper">
    <div v-for="(service, index) in services" :key="index">
      <div
        @click="
          (service.isActive = !service.isActive),
            service.isActive
              ? (total = total + service.price)
              : (total = total - service.price)
        "
        class="item"
        :class="[service.isActive ? activeClass : '']"
      >
        <p>{{ service.name }}</p>
        <span>${{ service.price }}</span>
      </div>
    </div>
    <div class="item item-total">
      <h3>Total:</h3>
      <h3>${{ total }}</h3>
    </div>
  </div>
</template>

<style lang="scss">
@import "src/assets/styles/main.scss";
</style>

<script lang="ts">
import Service from "@/models/ServicesModel";
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeView",
  data: () => ({
    activeClass: "active",
    services: [
      {
        name: "Web development",
        price: 300,
        isActive: false,
      },
      {
        name: "Design",
        price: 400,
        isActive: false,
      },
      {
        name: "Integration",
        price: 250,
        isActive: false,
      },
      {
        name: "Training",
        price: 220,
        isActive: false,
      },
    ] as Service[],
    total: 0,
  }),
});
</script>
