<template>
    <button>Hit me again <img id="character-icon" class="spin" src="/images/icons/arrow-icon.svg" alt="Circle arrow icon"></button> 
</template>

<style scoped>
button {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background-color: var(--character-color);
    color: var(--white-80);
    text-align: center;
    text-transform: uppercase;
    font-size: 1rem;
    line-height: 1;
    font-weight: 600;
    margin-top: 1.5rem;
    padding: 0.75rem 1.5rem;
    border: none;
    border-radius: 1.25rem;
    cursor: pointer;
    transition: background-color var(--transition-duration) var(--transition-timing);
}

@keyframes spin {
    from {transform: rotate(0deg);}
    to {transform: rotate(360deg)}
}

.spin img {
    animation-name: spin;
    animation-duration: 0.5s;
}
</style>