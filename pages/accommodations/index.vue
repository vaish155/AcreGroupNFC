<template>
    <div>
        <NuxtLayout name = "main-pages">
            <div class = "mb-[280px]">
                <div class = "bg-primary-green py-5 rounded-b-xl pb-[35%]">
                    <img src = "/logo-alt.png" class = "mx-auto w-[15%]" alt = "logo" loading = "lazy"/>
                    <h1 class = "text-white drop-shadow-lg font-bold text-center font-[Roboto] text-2xl my-2 mb-10">Accommodations</h1> 
                </div>

                <div class = "-my-[45%]">
                    <div v-for = "acc in (accsList.data.value?.data as Accs[])">
                        <ImageCard 
                            :description="acc.description"
                            :title="acc.title"
                            :location="acc.location"
                            :image-link="acc.imageLink"
                            :mapLink="acc.mapLink"
                        />
                    </div>
                </div>
            </div>

        </NuxtLayout>
    </div>
</template>

<script setup lang = 'ts'>

    interface AccsResp {
        message? : string
        data? : Accs[]
    }

    interface Accs {
        description? : string,
        imageLink? : string,
        location? : string,
        mapLink? : string,
        phoneNumber? : string,
        rating? : string,
        title? : string
    }

    const accsList = await useFetch<AccsResp>("/api/accDetails/fetchAll");
</script>