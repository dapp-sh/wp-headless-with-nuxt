<script setup lang="ts">
const config = useRuntimeConfig()
const WP_URL_CONTENT = config.public.WP_URL_CONTENT

async function getPages() {
  const [data] = await $fetch<unknown[]>(`${WP_URL_CONTENT}/v2/pages`)

  return data
}

const page = await getPages()
</script>

<template>
  <div>
    <UAlert
      title="Hello headless wp"
      icon="i-lucide-terminal"
    />

    <code>
      <pre>
        {{ page }}
      </pre>
    </code>
  </div>
</template>
