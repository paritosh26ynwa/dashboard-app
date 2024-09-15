<script setup>
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { BarChart } from '@/components/ui/chart-bar'

const props = defineProps({
  data: { type: Array, required: true }
})

</script>

<template>
  <Card class="col-span-7">
    <CardHeader>
      <CardTitle>Overview</CardTitle>
    </CardHeader>
    <CardContent class="pl-2">
      <BarChart :data="data || []" :categories="['total']" :index="'name'" :rounded-corners="4" />
    </CardContent>
  </Card>
</template>