<script lang="ts">
    import type { PageData } from './$types'
    import {formatDate} from "$lib/utils";
    import HeadingBox from "$lib/components/HeadingBox.svelte";
    import SvelteSeo from "svelte-seo";
    import { page } from '$app/stores';

    let { data }: {
        data: PageData;
    } = $props();
</script>

<SvelteSeo
        title="{data.meta.title} - Lumi's guides"
        description={data.meta.description}
        keywords="lumi, jxtq, lumifae, discordlab, friday, enka.discord, enka.cards, developer, website"
        openGraph={{
        title: `${data.meta.title} - Lumi's guides`,
        description: data.meta.description,
        url: `https://jxtq.moe/guides/${data.meta.slug}`,
        type: "website",
        site_name: "Lumi's Website"
    }}
/>

<HeadingBox title="Guide" class="max-h-[50rem] max-w-[100rem] w-full h-full">
    {@const Component = data.content}
    <div class="overflow-auto xl:max-h-[47rem] max-h-[40rem]">
        <a href={$page.url.searchParams.get('home') === '1' ? '/' : '/guides'} class="float-right mr-4">Go back</a>
        <h1 class="text-2xl font-bold">{data.meta.title}</h1>
        <p class="text-gray-300">{formatDate(data.meta.date)}</p>
        <div class="mt-5 prose prose-invert max-w-none p-5">
            <Component />
        </div>
    </div>
</HeadingBox>
