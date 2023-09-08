<script>
    import { fade } from 'svelte/transition';
    import { onMount } from 'svelte';
	import Cursor from './Cursor.svelte';

    let audio
    let ready = false;
    onMount(() => {
        setTimeout(() => {
            ready = true
        }, 100);
    })

    const links = {
        "GitHub": {link: "https://github.com/tekkenkkk", icon: "github.svg"},
        "LastFM": {link: "https://www.last.fm/user/tekkenkkk", icon: "lastfm.svg"},
        "WakaTime": {link: "https://wakatime.com/@tekken", icon: "wakatime.svg"},
    }

    const contact = {
        "Discord": {link: "https://discord.gg/v2tWMWBE7q", icon: "discord.svg"},
        "Telegram": {link: "https://t.me/ywncz", icon: "telegram.svg"},
    }
</script>

<Cursor />

<main class="bg-[#231b1a] h-[100vh] w-[100vw] select-none">
    <audio src="meow.mp3" bind:this={audio}></audio>
    
    <div class="h-full w-full flex flex-col overflow-x-hidden">
        {#if ready}
            <div transition:fade={{ duration: 800 }} class="flex-grow w-full flex items-center justify-center flex-col pb-10 sm:pb-0">
                <img class="h-[30%] sm:h-[35%] pb-6 sm:pb-10" draggable="false" src="meow.png" alt="shiggy">

                <span class="mb-6 sm:pb-4">
                    Silly coder

                    <button class="text-[#ffcb82] hover:underline focus:bg-[#ffffff5e]" on:click={()=>{
                        audio.play()
                    }}>
                        @tekkenkkk
                    </button>
                </span>

                <div class="flex flex-col gap-3 sm:gap-5 sm:flex-row items-center">
                    {#each Object.entries(links) as [site, { link, icon }]}
                        <a href={link} target="_blank" class="bg-[#999e5c2b] flex items-center justify-center border border-[#999e5c2b] hover:bg-white hover:bg-opacity-25 hover:border-[#ffffff5e] focus:bg-[#ffffff5e] p-3 gap-2 sm:w-fit w-64 transition-all rounded-lg">
                            <img class="w-6 h-6 invert" src={icon} alt={site}>
                            <p>{site}</p>
                        </a>
                    {/each}
                </div>
        
                <div class="flex flex-col pt-3 sm:pt-5 gap-3 sm:gap-5 sm:flex-row items-center">
                    {#each Object.entries(contact) as [site, { link, icon }]}
                        <a href={link} target="_blank" class="bg-[#9e2a592b] flex items-center justify-center border border-[#9e2a592b] hover:bg-white hover:bg-opacity-25 hover:border-[#ffffff5e] focus:bg-[#ffffff5e] p-3 gap-2 sm:w-fit w-64 transition-all rounded-lg">
                            <img class="w-6 h-6 invert" src={icon} alt={site}>
                            <p>{site}</p>
                        </a>
                    {/each}
                </div>
            </div>
        {/if}
    
        <footer class="fixed bottom-0 w-full h-15 p-3 flex justify-center items-center bg-[#1b1312] text-[#ffcb82]">
            <p class="text-sm sm:text-base">Copyright &copy; 2023 <a class="hover:text-white transition-all underline rounded" href="https://github.com/tekkenkkk" target="_blank">tekkenkkk</a> All rights reserved.</p>
        </footer>
    </div>
</main>