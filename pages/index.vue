<template>
    <div class="flex max-lg:flex-col items-center gap-6">
        <div class="flex flex-col gap-6 w-full lg:w-1/2">
            <p class="text-3xl tracking-widest font-semibold font-Comfortaa">Добро пожаловать в наш интернет-магазин кроссовок!</p>
            <p>Ваш идеальный выбор для прогулок и пробежок. У нас вы найдете новейшие модели кроссовок от ведущих мировых брендов. Наслаждайтесь уникальными предложениями и экспертной поддержкой!</p>
        </div>
        <img src="/images/hero/index.jpg" alt="" class="w-full lg:w-1/2 rounded-xl">
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl tracking-widest font-semibold font-Comfortaa">Преимущества</p>
        <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-6">
            <div class="flex flex-col gap-6 rounded-xl p-4 border border-white/15 transition-all duration-500 hover:scale-105 bg-white/5 backdrop-blur-3xl">
                <div class="flex items-center gap-4">
                    <p class="font-Comfortaa">Широкий выбор</p>
                    <Icon class="text-3xl shrink-0 text-red-500/50" name="material-symbols:arrow-selector-tool"/> 
                </div>
                <p>У нас вы найдете все необходимое — от детских пар до самых эксклюзивных и редких кроссовок.</p>
            </div>
            <div class="flex flex-col gap-6 rounded-xl p-4 border border-white/15 transition-all duration-500 hover:scale-105 bg-white/5 backdrop-blur-3xl">
                <div class="flex items-center gap-4">
                    <p class="font-Comfortaa">Качество и надежность</p>
                    <Icon class="text-3xl shrink-0 text-red-500/50" name="material-symbols:shield"/> 
                </div>
                <p>Мы сотрудничаем только с проверенными брендами, такими как nike, adidas, asics, puma и другими.</p>
            </div>
            <div class="flex flex-col gap-6 rounded-xl p-4 border border-white/15 transition-all duration-500 hover:scale-105 bg-white/5 backdrop-blur-3xl">
                <div class="flex items-center gap-4">
                    <p class="font-Comfortaa">Профессиональная консультация</p>
                    <Icon class="text-3xl shrink-0 text-red-500/50" name="material-symbols:person-check"/> 
                </div>
                <p>Наши эксперты всегда готовы помочь вам с выбором кроссовок, исходя из ваших потребностей и бюджета.</p>
            </div>
            <div class="flex flex-col gap-6 rounded-xl p-4 border border-white/15 transition-all duration-500 hover:scale-105 bg-white/5 backdrop-blur-3xl">
                <div class="flex items-center gap-4">
                    <p class="font-Comfortaa">Конкурентные цены</p>
                    <Icon class="text-3xl shrink-0 text-red-500/50" name="material-symbols:price-check"/> 
                </div>
                <p>Мы предлагаем лучшие цены на рынке и регулярные скидки для наших клиентов.</p>
            </div>
        </div>
    </div>
    <div class="flex flex-col gap-6">
        <p class="text-3xl tracking-widest font-semibold font-Comfortaa">Наши новинки</p>
        <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-6">
            <div class="flex flex-col gap-6 bg-white/5 rounded-xl p-4 border border-white/15 backdrop-blur-3xl group" v-for="product in products">
                <div class="overflow-hidden rounded-xl">                    
                    <img :src="product.image" alt="" class="transition-all duration-500 group-hover:scale-125 w-full aspect-video object-cover">
                </div>
                <p class="text-2xl font-Comfortaa">{{ product.title }}</p>
                <div class="flex flex-col gap-2 mt-auto">
                    <p class="text-3xl font-Comfortaa">{{ product.price.toLocaleString() }} ₽</p>
                    <NuxtLink :to="`/catalog/product-${product.id}`" class="mx-auto flex flex-col w-fit after:w-0 after:bg-white after:h-px after:transition-all after:duration-500 group-hover:after:w-full">Подробнее...</NuxtLink>
                </div>
            </div>
        </div>
    </div>
   
</template>

<script setup>
    /* подключение БД */
    const supabase = useSupabaseClient() 

    const { data, error } = await supabase
    .from('products')
    .select('*')

    const products = ref(data.slice(0,4))
</script>