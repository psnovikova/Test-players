<template>
  <transition name="slide-fade">
    <div v-if="isVisible" class="alert">{{ message }}</div>
  </transition>
</template>

<script>
export default {
  name: "ErrorMessage",
  props: {
    message: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      isVisible: false,
    };
  },
  methods: {
    showAlert() {
      this.isVisible = true;
      setTimeout(() => {
        this.isVisible = false;
      }, 2000);
    },
  },
  mounted() {
    if (this.message) {
      this.showAlert();
    }
  },
};
</script>

<style scoped>
.alert {
  position: fixed;
  top: 20px;
  right: 20px;
  background-color: #d32f2f;
  color: #fff;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  font-size: 14px;
  opacity: 0.9;
  transition: opacity 0.5s ease;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.5s ease;
}

.slide-fade-enter,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>
