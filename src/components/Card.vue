<script>
</script>

<template>
    <div class="card">
        <!-- TODO: Dynamically load random character and quote from API-->
        <h1>Michael Scott</h1>
        <h2>Well, Happy Birthday Jesus. Sorry your party’s so lame.</h2>
        <img src="@/assets/images/coffee-icon.svg" alt="Coffee icon">
    </div>
</template>

<style scoped> 
    .card {
        background-color: var(--character-color);
        color: var(--white);
        text-align: center;
        border-radius: 1.5rem;
        padding: 1.5rem 2.125rem;
    }
    h1 {
        color: var(--white-80);
        font-size: 0.875rem; 
        font-weight: 600;
        line-height: 1;
        margin: 0 0 .625rem 0;
        text-transform: uppercase;
    }
    h2 {
        font-size: 1.125rem;
        font-weight: 900;
        line-height: 1.5;
        margin: 0 0 1.5rem 0;
        text-transform: uppercase;
    }
</style>