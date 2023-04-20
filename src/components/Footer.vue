<template>
     <footer> 
        <p>
            Built with <a href="https://www.officeapi.dev/">the Office API</a> – View <a href="https://github.com/elysenewland/thats-what-the-office-said">Github</a>
        </p>
    </footer>
</template>

<style scoped>
footer {
    background-color: var(--character-color);
    padding: 0.75rem 1.5rem;
    color: var(--white-80);
    font-weight: 400;
    font-size: 0.75rem;
    line-height: 1;
    text-align: center;
}

@media (min-width: 800px) {
    footer{
        text-align: right;
    }
}

p {
    margin: 0;
}

a {
    color: inherit;
}
</style>