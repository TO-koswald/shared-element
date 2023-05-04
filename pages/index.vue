<template>
  <div class="max-w-4xl mx-auto mb-4">
    <label class="relative block">
      <input
        class="placeholder:italic placeholder:text-slate-400 block bg-white w-full border border-slate-300 rounded-md py-2 pl-9 pr-3 shadow-sm focus:outline-none focus:border-sky-500 focus:ring-sky-500 focus:ring-1 sm:text-sm"
        placeholder="Search..." type="text" name="search" v-model="search" />
      </label>
    </div>

    <NuxtLink v-for="room in filteredRooms" :to="'/' + room.id">
      <RoomItem :room="<Room>room" />
    </NuxtLink>
</template>
<script setup lang="ts">
import rooms from "@/data";

const search = ref("");

const filteredRooms = computed(() => {
  let result = rooms;
 
  if (search.value) {
    result = result.filter((room) =>
      room.name.toLowerCase().includes(search.value.toLowerCase())
    );
  }
  return result;
});
</script>
