<script>
// Export props in order to pass them into Card component
export default {
    props: {
        avatar: {
            type: String, 
            default: "",
        },
        icon: {
            type: String, 
            default: "",
        },
        iconName: {
            type: String, 
            default: "",
        },
        subhead: String,
        title: String,
        body: String 
   }
}
</script>

<template>
    <!-- Dynamically pass in the characterColor from app.vue and update the CSS variable -->
    <div class="card">
        <img v-if="avatar" class="avatar" :src="avatar" :alt="subhead + ' Avatar'" loading="lazy" width="150" height="150" />
        <h1 v-if="subhead">{{ subhead }}</h1>
        <h2 v-if="title">{{ title }}</h2>
        <p v-if="body">{{ body }}</p>
        <img v-if="icon" :src="icon" :alt="iconName">
    </div>
</template>

<style scoped> 
    .card {
        background-color: var(--character-color);
        color: var(--white);
        text-align: center;
        border-radius: 1.5rem;
        padding: 2.125rem 1.5rem;
        transition: background-color var(--transition-duration) var(--transition-timing);
    }

    .avatar {
        margin-bottom: 1.15rem;
        max-width: 9.375rem;
        border-radius: 100%;
        background-color: var(--white-25);
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