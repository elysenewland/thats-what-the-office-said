<script>
// Export props in order to pass them into Card component
export default {
    props: {
        subhead: String,
        title: String,
        body: String      
    }
}
</script>

<template>
    <div class="card">
        <h1 v-if="subhead">{{ subhead }}</h1>
        <h2 v-if="title">{{ title }}</h2>
        <p v-if="body">{{ body }}</p>
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