<script lang="ts">
    import type { PageData } from './$types';
    import {formatDate} from "$lib/utils";
    import HeadingBox from "$lib/components/HeadingBox.svelte";
    import SvelteSeo from "svelte-seo";

    let { data }: {
        data: PageData;
    } = $props();
</script>

<SvelteSeo
        title="Lumi's Projects"
        description="My projects on GitHub"
        keywords="lumi, jxtq, lumifae, discordlab, friday, enka.discord, enka.cards, developer, website"
        openGraph={{
        title: "Lumi's Projects",
        description: "My projects on GitHub",
        url: "https://jxtq.moe/projects",
        type: "website",
        site_name: "Lumi's Website"
    }}
/>

<HeadingBox title="Projects" class="max-h-[51rem] max-w-[100rem] w-full h-full">
    <div class="overflow-y-scroll h-full">
        <a href="/" class="float-right">Go back</a>
        <div class="mt-10 space-y-4">
            {#each data.repos as repo}
                <a href="https://github.com/{repo.author}/{repo.name}" class="block rounded-[13px] p-4 h-auto w-full border-2 border-[#7A7A7A]">
                    <h1 class="font-bold text-xl">{repo.name}</h1>
                    <p class="text-gray-300">{repo.language} Project</p>
                    <p>{repo.description}</p>
                </a>
            {/each}
        </div>
    </div>
</HeadingBox>
