<script>
    import {Navbar} from "flowbite-svelte";
    import {Heading, Card, P} from "flowbite-svelte";
    import VerticalLine from "./VerticalLine.svelte";
    import {DarkMode} from "flowbite-svelte";
    import HorizontalLine from "./HorizontalLine.svelte";
    import pages from "./pages.svelte";
    import {_, addMessages, init, getLocaleFromNavigator} from 'svelte-i18n';
    import en from "./locale/en.json";
    import de from "./locale/de.json";

    addMessages('en', en);
    addMessages('de', de);
    init({
        fallbackLocale: 'en',
        initialLocale: getLocaleFromNavigator(),
    });

    function openLink(link) {
        window.open(link, "_self");
    }
</script>
<main class="min-h-screen bg-white dark:bg-gray-900 text-gray-900 dark:text-white transition-colors">
    <Navbar class="px-8 bg-green-600 dark:bg-green-700 shadow-md">
        <div class="w-full flex justify-end">
            <DarkMode class="bg-white hover:bg-gray-200 dark:hover:bg-gray-200"/>
        </div>
    </Navbar>
    <div class="p-8 items-center flex justify-center flex-wrap gap-4">
        <Card class="max-w-min p-4">
            <Heading class="whitespace-nowrap text-2xl md:text-4xl lg:text-5xl">
                {@html $_('title')}
            </Heading>
            <HorizontalLine/>
            <P class="mt-4 mb-4 text-lg sm:px-8 dark:text-gray-300">
                {@html $_('description')}
            </P>
        </Card>
        <div class="flex flex-col items-center">
            {#each pages as obj}
                {@const Icon = obj.icon}
                {@const link = obj.link}
                <button on:click={() => openLink(link)}
                        class="[&:not(:first-child)]:mt-4 p-4 border rounded-lg max-w-sm
                        shadow-md rounded-lg w-full flex gap-4 items-center
                        border-gray-200
                        dark:border-gray-700 dark:bg-gray-800 bg-white
                        hover:bg-gray-100 active:ring-4 active:ring-gray-200
                        dark:hover:bg-gray-500 active:ring-4 active:ring-gray-400">
                    <Icon/>
                    <VerticalLine/>
                    {obj.text}
                    {#if obj.old}
                        ({$_('old')})
                    {/if}
                </button>
            {/each}
        </div>
    </div>
</main>