<script lang="ts">
    export let click: any
</script>
<button class=" bg-slate-200 py-[10px] w-full rounded-[7px] border-slate-400 border-[2.2px]" on:click={click}>
    <slot />
</button>