<script setup>
import { Skeleton } from '@/components/ui/skeleton'

</script>

<template>
  <div class="grid gap-4 lg:grid-cols-4">
    <Skeleton class="h-[175px] w-[325px] rounded-xl" />
    <Skeleton class="h-[175px] w-[325px] rounded-xl" />
    <Skeleton class="h-[175px] w-[325px] rounded-xl" />
    <Skeleton class="h-[175px] w-[325px] rounded-xl" />
  </div>
  <div class="grid gap-4 lg:grid-cols-2">
    <Skeleton class="h-[425px] rounded-xl" />
    <Skeleton class="h-[425px] rounded-xl" />
  </div>
</template>