<script setup lang="ts">
const { search } = storeToRefs(useTempHomeStore())

const input = ref<HTMLElement | null>(null)
const inputValue = ref('')

onBeforeMount(() => {
  search.value.keywords = ''
})

const debouncedSearch = debounce((inputValue: string) => {
  if (inputValue.trim()) {
    search.value.keywords = inputValue
  } else {
    search.value.keywords = ''
  }
}, 300)

watch(
  () => search.value.keywords,
  () => {
    if (!inputValue.value) {
      inputValue.value = search.value.keywords
    }
  }
)

onMounted(() => {
  if (input) {
    input.value?.focus()
  }
})
</script>

<template>
  <div class="search-form">
    <input
      ref="input"
      v-model="inputValue"
      type="search"
      class="input"
      :placeholder="`${$t('home.header.search')}`"
      @input="debouncedSearch(inputValue)"
      @keydown.enter="debouncedSearch(inputValue)"
    />
  </div>
</template>

<style lang="scss" scoped>
.search-form {
  position: sticky;
  top: 0;
  width: 100%;
  max-width: 777px;

  @include kun-blur;
  @include kun-center;
  box-shadow: none;
}

.input {
  padding: 0 15px;
  height: 40px;
  width: 100%;
  font-size: 16px;
  border: none;
  background-color: transparent;
  border: 2px solid var(--kungalgame-blue-5);
  border-radius: 10px;
  color: var(--kungalgame-font-color-3);
  transition: all 0.2s;

  &:focus {
    border: 2px solid var(--kungalgame-pink-4);
  }

  &::placeholder {
    color: var(--kungalgame-font-color-1);
  }
}
</style>
