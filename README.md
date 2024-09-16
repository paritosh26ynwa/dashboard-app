# Metadata Driven Dashboard UI - Documentation

## Project Overview

This project demonstrates a metadata-driven UI using Vue.js, where the UI components are dynamically generated based on metadata provided by an external source. The app showcases various components like metric cards, charts, and data tables, with fallbacks implemented to handle unsupported component types and missing data.

This solution is designed to be modular, extendable, and fault-tolerant, ensuring that the app gracefully handles incomplete or erroneous metadata.

## Demo

Have a look at this [link to see the demo in action.](https://starlit-dango-097120.netlify.app/)

## Tech Stack

- [Vue.js](https://vuejs.org/)
- [TailwindCSS](https://tailwindcss.com/)
- [Shadcn UI](https://ui.shadcn.com/)

## Solution Overview

The core idea behind the solution is to:
- Input Data Structure: Define a JSON structure that external sources can follow to render the UI.
- Dummy Components: Create reusable components that are rendered dynamically based on the metadata.
- Metadata Processor: Design a central function/component to process metadata and dynamically build the view.
- Data Flow Support: Ensure data can be passed between components (e.g., through event emissions or props).

## 1. Input Structure

The app is driven by an external JSON that contains the layout and data for each component. Here's an example of how the input JSON is structured:

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

## 2. Dummy Components

We have defined the following components for this demo:
- LoaderCompoent: Displays a loader skeleton to mock an API call
- MetricComponent: Displays metric details such as revenue count, active user count etc.
- OverviewComponent: Displays a bar chart
- SalesComponent: Displays a data table

Each component defines props and fallback values to ensure the component renders correctly even if the external data is missing some fields.

## 3. Metadata Processor

The App.vue component is responsible for fetching the metadata and rendering the appropriate component based on the type defined in the metadata. It dynamically selects the correct component or a fallback if the type is unsupported.

## 4. Data Flow Support

Data can be passed between components through props

## What Could Go Wrong (WCGW) Scenarios
- Incorrect Metadata: If the external source provides incorrect metadata (e.g., a missing or unknown component type), it could break the UI. A good fallback would be to show a default component or error message when an unsupported type is encountered.
- Data Mismatch: If the data structure expected by a component differs from what is provided (e.g., a missing type), it could result in broken functionality. Ensure that the data structure is validated before rendering the component.
- Performance Issues: With a large amount of metadata or components, rendering could become slow. Consider optimizations such as lazy loading components.
- State Management: Handling shared data between dynamically created components could be tricky, especially as the app scales. Vue’s event system or Vuex can help manage shared states effectively.