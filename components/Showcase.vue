<template>
  <div v-if="!$parent.is_mobile" class="showcase-container">
    <img :src="$parent.album.cover" alt="cover" />
    <div>
      <h1>{{ $parent.current_track.title }}</h1>
      <h2>
        {{ $parent.current_track.artist
        }}<span v-show="$parent.album.type != 'mixtape'">
          • {{ $parent.album.name }}</span
        >
      </h2>
    </div>
    <div class="extra-controls" @click="$parent.openExpansionPanel('albums')">
      <h4>more albums</h4>
      <svg
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="1.5"
      >
        <circle cx="12" cy="12" r="10"></circle>
        <circle cx="12" cy="12" r="3"></circle>
      </svg>
    </div>
    <svg
      v-if="$parent.player_state == 3"
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      stroke-width="1.5"
    >
      <polyline points="23 4 23 10 17 10"></polyline>
      <polyline points="1 20 1 14 7 14"></polyline>
      <path
        d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"
      ></path>
    </svg>
  </div>
  <div v-else class="showcase-container">
    <h1 class="text-2xl">{{ $parent.current_track.title }}</h1>
    <h2>
      {{ $parent.current_track.artist }}
    </h2>
  </div>
</template>

<script>
export default {};
</script>

<style lang="postcss">
.showcase-container {
  @apply pt-32 flex flex-col items-center justify-between;

  @media (min-width: 768px) {
    @apply h-28 pt-0 flex-row justify-start;
  }
}
.showcase-container * {
  @media (min-width: 768px) {
    @apply my-auto;
  }
}
.showcase-container img {
    @apply h-full;
}
.showcase-container div {
  @media (min-width: 768px) {
    @apply ml-4;
  }
}
.showcase-container .extra-controls svg {
  @media (min-width: 768px) {
    @apply h-8 w-8 ml-4;
  }
}
.showcase-container > svg {
  @media (min-width: 768px) {
    @apply h-10 w-10 ml-8;
    @apply opacity-60;

    animation-name: spin;
    animation-duration: 1.41s;
    animation-iteration-count: infinite;
  }
}
.showcase-container :nth-child(3n) {
  @media (min-width: 768px) {
    @apply ml-auto;
  }
}
.extra-controls {
  @media (min-width: 768px) {
    @apply pl-4 py-1 opacity-0 rounded-full;
    @apply flex items-center;
    @apply cursor-pointer;
    transition: opacity 0.2s;
  }
}
.extra-controls:hover {
  @media (min-width: 768px) {
    background: #00000033;
  }
}
.extra-controls:active {
  @media (min-width: 768px) {
    background: #00000066;
  }
}
.page-container:hover .extra-controls {
  @media (min-width: 768px) {
    @apply opacity-70;
  }
}
</style>