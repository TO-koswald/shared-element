<template>
  <div
    class="max-w-4xl mx-auto mb-4 flex flex-col items-center bg-white border border-gray-200 rounded-lg shadow md:flex-row sm:mx-2 md-mx-0 md:max-w-4xl hover:bg-gray-100">
    <img class="object-fill min-w-[300px] rounded-t-lg min-h-full md:h-auto md:w-48 md:rounded-none md:rounded-l-lg"
      :src="room.images[0]" />
    <div class="flex flex-col justify-between p-4 leading-normal">
      <div class="flex flex-row">
        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ room.name }}</h5>
        <span class="flex-grow text-blue-500 text-2xl text-right">${{ room.price }}</span>
      </div>
      <div class="flex flex-row mb-2">
        <div>
          <p> {{ room.minGuestCount - room.maxGuestCount !== 0 ? `${room.minGuestCount} -` : }} {{ room.maxGuestCount }}
          </p>
        </div>
        <div>
          <p> Size: {{ room.roomSize }} m²</p>
        </div>
      </div>
      <div class="flex flex-row flex-wrap mb-2">
        <Tag v-for="tag in room.tags">{{ tag }}</Tag>
      </div>
      <div class="flex flex-row max-h-8">
        <p
          class="text-ellipsis break-words overflow-hidden flex-grow max-h-8 mb-3 font-normal text-gray-700 dark:text-gray-400">
          {{ room.description }}</p>

      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { RoomItem } from '~~/.nuxt/components';

defineProps<{
  room: Room;
}>();



</script>
