<script setup>
import { Package2, Search } from 'lucide-vue-next'
import { Input } from '@/components/ui/input'
import { Button } from '@/components/ui/button'
import LoaderCompoent from './components/LoaderCompoent.vue'
import MetricCardComponent from './components/MetricComponent.vue'
import OverviewComponent from './components/OverviewComponent.vue'
import SalesComponent from './components/SalesComponent.vue'
import { reactive, ref } from 'vue'

const isLoading = ref(true)
let metadata = reactive({})
setTimeout(() => {
  metadata = {
    heading: 'Dashboard',
    components: [
      {
        type: 'metric',
        data: [
          {
            title: 'Total Revenue',
            content: '$45,231.89',
            subContent: '+20.1% from last month',
          },
          {
            title: 'Subscriptions',
            content: '+2350',
            subContent: '+180.1% from last month',
          },
          {
            title: 'Sales',
            content: '+12,234',
            subContent: '+19% from last month',
          },
          {
            title: 'Active Now',
            content: '+573',
            subContent: '+201 since last hour',
          },
        ],
      },
      {
        type: 'overview',
        data: [
          { name: 'Jan', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Feb', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Mar', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Apr', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'May', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Jun', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Jul', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Aug', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Sep', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Oct', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Nov', total: Math.floor(Math.random() * 5000) + 1000 },
          { name: 'Dec', total: Math.floor(Math.random() * 5000) + 1000 },
        ]
      },
      {
        type: 'sales',
        data: [
          {
            name: "Olivia Martin",
            initials: 'OM',
            email: 'olivia.martin@email.com',
            amount: '+$1,999.00'
          },
          {
            name: "Jackson Lee",
            initials: 'JL',
            email: 'jackson.lee@email.com',
            amount: '+$39.00'
          },
          {
            name: 'Isabella Nguyen',
            initials: 'IN',
            email: 'isabella.nguyen@email.com',
            amount: '+$299.00'
          },
          {
            name: 'William Kim',
            initials: 'WK',
            email: 'will@email.com',
            amount: '+$99.00'
          },
          {
            name: 'Sofia Davis',
            initials: 'SD',
            email: 'sofia.davis@email.com',
            amount: '+$39.00'
          },
        ]
      }
    ],
  };
  isLoading.value = false
}, 2000)

const getComponent = (type) => {
  const components = {
    metric: MetricCardComponent,
    overview: OverviewComponent,
    sales: SalesComponent
  }
  return components[type] || null
}

</script>

<template>
  <div class="flex min-h-screen w-full flex-col">
    <header class="sticky top-0 flex h-16 items-center gap-4 border-b bg-background px-4 md:px-6">
      <nav
        class="hidden flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6">
        <a href="#" class="flex items-center gap-2 text-lg font-semibold md:text-base">
          <Package2 class="h-6 w-6" />
          <span class="sr-only">Acme Inc</span>
        </a>
        <a href="#" class="text-foreground transition-colors hover:text-foreground">
          Dashboard
        </a>
        <a href="#" class="text-muted-foreground transition-colors hover:text-foreground">
          Orders
        </a>
        <a href="#" class="text-muted-foreground transition-colors hover:text-foreground">
          Products
        </a>
        <a href="#" class="text-muted-foreground transition-colors hover:text-foreground">
          Analytics
        </a>
      </nav>
      <div class="flex w-full items-center gap-4 md:ml-auto md:gap-2 lg:gap-4">
        <form class="ml-auto flex-1 sm:flex-initial">
          <div class="relative">
            <Search class="absolute left-2.5 top-2.5 h-4 w-4 text-muted-foreground" />
            <Input type="search" placeholder="Search products..." class="pl-8 sm:w-[300px] md:w-[200px] lg:w-[300px]" />
          </div>
        </form>
      </div>
    </header>

    <main class="flex-1 space-y-4 p-8 pt-6">
      <template v-if="isLoading">
        <LoaderCompoent />
      </template>
      <template v-else>
        <div class="flex items-center justify-between space-y-2">
          <h2 class="text-3xl font-bold tracking-tight">
            {{ metadata.heading }}
          </h2>
          <div class="flex items-center space-x-2">
            <Button>
              Download
            </Button>
          </div>
        </div>
        <div class="grid gap-4 grid-cols-12">
          <component v-for="(block, index) in metadata.components" :key="index" :is="getComponent(block.type)"
            :data="block.data">
          </component>
        </div>
      </template>
    </main>
  </div>
</template>

<style scoped></style>
