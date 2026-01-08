<template>
  <div class="translation-block">
    <div
      class="chinese-text"
      :class="{ 'is-expanded': isExpanded }"
      @click="toggleEnglish"
    >
      <slot name="chinese" />
    </div>
    <transition name="slide-fade">
      <div
        v-if="isExpanded"
        class="english-text"
      >
        <slot name="english" />
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isExpanded = ref(false)

const toggleEnglish = () => {
  isExpanded.value = !isExpanded.value
}
</script>

<style scoped>
.chinese-text {
  cursor: pointer;
  position: relative;
}

.toggle-icon {
  font-size: 0.875rem;
  margin-left: 0.5rem;
  opacity: 0.6;
  transition: opacity 0.2s;
}

.chinese-text:hover .toggle-icon {
  opacity: 1;
}

.english-text {
  margin-top: 0.75rem;
  padding: 1rem;
  background-color: #f8f9fa;
  border-radius: 4px;
  line-height: 1.6;
  color: #555;
  font-style: italic;
  border-left: 2px solid #dee2e6;
}

/* 展开/收起动画 */
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.2s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-10px);
  opacity: 0;
}

/* 代码样式 */
.english-text :deep(code) {
  background-color: #e8e8e8;
  padding: 0.125rem 0.375rem;
  border-radius: 3px;
  font-family: 'Consolas', 'Monaco', monospace;
  font-style: normal;
}
</style>
