<template>
    <div>
        <div class="bg-gray-700 rounded-lg mt-7 mx-2 p-8 max-w-2xl md:mx-auto fonsa">
            <button class="rounded-full bg-gray-300 flex p-1 mx-auto focus:outline-none">
                <button 
                    @click="period = 'monthly'" 
                    class="px-2 md:px-5 py-1 rounded-full uppercase text-sm font-bold focus:outline-none"
                    :class="period === 'monthly' ? 'bg-blue-600 text-white': ''"
                    >Monthly</button>
                <button 
                    @click="period = 'yearly'" 
                    class="px-2 md:px-5 py-1 rounded-full uppercase text-sm font-bold focus:outline-none"
                    :class="period === 'yearly' ? 'bg-blue-600 text-white': ''"
                    >Yearly</button>
            </button>
            <div class="text-white md:flex justify-center mt-6 text-center md:text-left">
                <div class="md:flex w-full">
                    <div v-for="plan in plans" :key="plan.p" class="md:w-1/3">
                        <h1 class="text-2xl font-semibold my-4">{{ plan.name }}</h1>
                        <ul>
                            <li v-for="benefit in plan.benefits[period]" :key="benefit">{{ benefit }}</li>
                        </ul>
                        <div class="flex my-6">
                            <h1 class="text-4xl font-bold">${{ plan.pricing[period].price }}</h1>
                            <p class="text-gray-400">{{ plan.pricing[period].frequency }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div> 
    </div>
</template>

<script>
export default {
    data() {
        return {
            period: 'monthly',
            plans: [
                {
                    name: 'Basic',
                    benefits: {
                        monthly: ['Live Chat', '3 hours per day', 'Up to 100 Viewers'],
                        yearly: ['Live Chat', '3 hours per day', 'Up to 100 Viewers', 'Schedule Events']
                    },
                    pricing: { 
                        monthly: { price: 9.99, frequency: '/mo'},
                        yearly: { price: 99.00, frequency: '/yr'}
                    }
                },
                {
                    name: 'Premium',
                    benefits: {
                        monthly: ['Live Chat', '12 hours per day', 'Up to 500 Viewers'],
                        yearly: ['Live Chat', '12 hours per day', 'Up to 500 Viewers', 'Schedule Events']
                    },
                    pricing: {
                        monthly: { price: 19.99, frequency: '/mo'},
                        yearly: { price: 199.00, frequency: '/yr'}
                    }
                },
                {
                    name: 'Pro',
                    benefits: {
                        monthly: ['Live Chat', '24 hours per day', 'Unlimited Viewers'],
                        yearly: ['Live Chat', '24 hours per day', 'Unlimited Viewers', 'Schedule Events']
                    },
                    pricing: {
                        monthly: { price: 49.99, frequency: '/mo'},
                        yearly: { price: 499.00, frequency: '/yr'}
                    }
                }
            ]
        }
    }
}
</script>