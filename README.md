# Metadata Driven Dashboard UI

This is a demo app that displays UI based on the data provided by an external source.
## Demo

Have a look at this [link to see the demo in action.](https://verdant-twilight-a26876.netlify.app/)


## Tech Stack

- [Vue.js](https://vuejs.org/)
- [TailwindCSS](https://tailwindcss.com/)
- [Shadcn UI](https://ui.shadcn.com/)

## Metadata

```
{
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
}
```
