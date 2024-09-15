<script setup>
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Avatar, AvatarFallback, AvatarImage } from '@/components/ui/avatar'

const props = defineProps({
  data: { type: Array, required: true }
})

</script>

<template>
  <Card class="col-span-5">
    <CardHeader>
      <CardTitle>Recent Sales</CardTitle>
      <CardDescription>
        You made 265 sales this month.
      </CardDescription>
    </CardHeader>
    <CardContent>
      <div class="space-y-8">
        <div v-for="(item, index) in data" :key="index" class="flex items-center">
          <Avatar class="h-9 w-9">
            <AvatarImage src="/avatars/01.png" alt="Avatar" />
            <AvatarFallback>{{ item.initials }}</AvatarFallback>
          </Avatar>
          <div class="ml-4 space-y-1">
            <p class="text-sm font-medium leading-none">
              {{ item.name }}
            </p>
            <p class="text-sm text-muted-foreground">
              {{ item.email }}
            </p>
          </div>
          <div class="ml-auto font-medium">
            {{ item.amount }}
          </div>
        </div>
      </div>
    </CardContent>
  </Card>
</template>