<script>
    import {Navbar} from "flowbite-svelte";
    import {Heading, Card, P, A, Mark, Secondary} from "flowbite-svelte";
    import {
        CameraPhotoOutline,
        KeyboardOutline,
        LightbulbOutline,
        PersonChalkboardOutline
    } from "flowbite-svelte-icons"
    import VerticalLine from "./VerticalLine.svelte";
    import {DarkMode} from "flowbite-svelte";
    import HorizontalLine from "./HorizontalLine.svelte";

    const links = [
        {
            icon: KeyboardOutline,
            text: "SQLite-WebUI",
            link: "./SQLite-WebUI/"
        },
        {
            icon: LightbulbOutline,
            text: "JSMindmap",
            link: "./JSMindmap/"
        },
        {
            icon: PersonChalkboardOutline,
            text: "JSMultiLayerPerceptron",
            link: "./JSMultiLayerPerceptron"
        },
        {
            icon: CameraPhotoOutline,
            text: "FFmpegWebUI",
            link: "./FFmpegWebUI/"
        }
    ]

    function openLink(link) {
        window.open(link, "_self");
    }
</script>
<main class="min-h-screen bg-white dark:bg-gray-900 text-gray-900 dark:text-white transition-colors">
    <Navbar class="px-8">
        <div class="w-full flex justify-end">
            <DarkMode class="bg-gray-300"/>
        </div>
    </Navbar>
    <div class="p-8 items-center flex justify-center flex-wrap gap-4">
        <Card class="max-w-min p-4">
            <Heading class="whitespace-nowrap text-2xl md:text-4xl lg:text-5xl">Projects Overview</Heading>
            <HorizontalLine />
            <P class="mt-4 mb-4 text-lg sm:px-8 dark:text-gray-300">
                A collection of some of my projects
                which are hosted with Github.io Pages.
            </P>
            <P class="mt-4 mb-4 text-lg sm:px-8 dark:text-gray-300">
                Feel free to try them out, fork them or make pull requests.
            </P>
        </Card>
        <div class="flex flex-col items-center">
            {#each links as obj}
                {@const Icon = obj.icon}
                {@const link = obj.link}
                <button on:click={() => openLink(link)}
                        class="mt-4 p-4 border rounded-lg max-w-sm shadow-md
                        rounded-lg w-full flex gap-4 items-center
                        border-gray-200
                        dark:border-gray-700 dark:bg-gray-800 bg-white
                        hover:bg-gray-100 active:ring-4 active:ring-gray-200
                        dark:hover:bg-gray-500 active:ring-4 active:ring-gray-400">
                    <Icon/>
                    <VerticalLine/>
                    {obj.text}
                </button>
            {/each}
        </div>
    </div>
</main>
