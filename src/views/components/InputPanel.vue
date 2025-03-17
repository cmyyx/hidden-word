<script setup>
import {useI18n} from 'vue-i18n';
import ClearableTextarea from '../../components/ClearableTextarea.vue';
import {useAppStore} from '@/store/index.js';

const {t} = useI18n();
const store = useAppStore();
</script>

<template>
  <div
      class="bg-white/80 backdrop-blur-sm rounded-xl shadow-md border border-indigo-100/50 overflow-hidden transition-all duration-300 hover:shadow-lg">
    <div class="px-5 py-4">
      <div class="flex items-center mb-3">
        <i :class="store.isEncoding ? 'fa-solid fa-keyboard text-indigo-500' : 'fa-solid fa-magnifying-glass text-indigo-500'"
           class="mr-2"></i>
        <h3 class="text-indigo-900 font-medium text-sm">
          {{ store.isEncoding ? t('input.encodeTitle') : t('input.decodeTitle') }}
        </h3>
      </div>

      <ClearableTextarea
          v-model="store.inputText"
          :placeholder="store.isEncoding ? t('input.encodePlaceholder') : t('input.decodePlaceholder')"
          min-height="120px"
      />
    </div>
  </div>
</template>
