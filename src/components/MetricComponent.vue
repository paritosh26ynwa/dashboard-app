<script setup>
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { computed } from 'vue';

const props = defineProps({
  data: { type: Array, required: true }
})


const hasEvenCards = computed(() => props.data.length % 2 === 0 ? true : false)
</script>

<template>
  <Card v-for="(card, index) in data" :key="index" class="col-span-4" :class="{ 'col-span-3': hasEvenCards }">
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <CardTitle class="text-sm font-medium">
        {{ card.title }}
      </CardTitle>
    </CardHeader>
    <CardContent>
      <div class="text-2xl font-bold">
        {{ card.content }}
      </div>
      <p class="text-xs text-muted-foreground">
        {{ card.subContent }}
      </p>
    </CardContent>
  </Card>
</template>