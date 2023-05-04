<template>
  <div>

    <NuxtLink class="lowercase font-bold" to="/">Go Back</NuxtLink>
    <div v-if="!room">Room {{ id }} not found</div>
    <div v-else class="p-5 shadow-md rounded-md bg-white my-4">
      <div class="flex flex-row">

        <div v-if="sortedImages" class="mr-4 flex sm:flex-row flex-col max-h-[500px] sm:w-full md:w-3/4  overflow-y-auto">
          <img :src="sortedImages[0]" class="h-[500px] w-full min-w-[75%] object-cover rounded-md" />
        </div>
        <div class="flex sm:flex-row flex-col space-y-2 max-h-[500px] md:w-1/4 overflow-scroll">
          <div class="grid md:grid-cols-1 gap-2">
            <img v-for="img in otherImages" @click="setMainImage(img)" :src="img"
              class="h-[300px] w-full object-cover rounded-md" />
          </div>
        </div>
      </div>
      <div class="flex flex-col mt-4">
        <div class="flex flex-row justify-between">
          <h1 class="text-2xl">{{ room.name }}</h1>
          <div class="justify-end">
            <div class="text-blue-500 text-3xl">${{ room.price }}</div>
          </div>

        </div>
        <div class="flex flex-wrap space-x-2 flex-shrink-0">
          <Tag v-for="tag in room.tags">{{ tag }}</Tag>
        </div>
        <p class="text-ellipsis break-words overflow-hidden flex-grow mt-2">
          {{ room.description }}
        </p>

      </div>

    </div>
  </div>
</template>

<script setup lang="ts">
import rooms from "@/data";

const { id } = useRoute().params;
const room = rooms.find((room) => room.id === Number(id));
const otherImages = computed(() => room?.images.slice(1, room.images.length));

const sortedImages = ref(room?.images)

const setMainImage = (img: string) => {
  console.log(img);
  if (sortedImages.value) {
    sortedImages.value.unshift(img)
  }

  // const index = room.images.indexOf(img)
  // const element = room?.images.splice(index,1)[0]
  // console.log('element:', element);

  // const sorted =  room?.images.splice(0, 0, element)

  // console.log(sorted);

  // sortedImages.value = sorted

}

</script>
