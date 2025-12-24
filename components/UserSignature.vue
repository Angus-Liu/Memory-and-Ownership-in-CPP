<template>
  <div
    class="abs-bl ml-14 mb-12 flex items-center
           cursor-pointer select-none
           hover:opacity-85 transition-opacity"
    @click="openLink"
  >
    <img
      :src="avatar"
      alt="avatar"
      class="rounded-full w-15 h-15 object-cover"
    />
    <div class="ml-3 flex flex-col text-left">
      <span class="font-300">{{ displayName }}</span>
      <span>{{ username }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    avatar?: string
    displayName?: string
    username?: string
    link?: string
  }>(),
  {
    avatar: 'https://avatars.githubusercontent.com/u/24972887?v=4',
    displayName: '程序员小刀',
    username: 'Angus-Liu',
    link: 'https://github.com/Angus-Liu',
  }
)

function openLink() {
  window.open(props.link, '_blank')
}
</script>