<template>
     <footer> 
        <p>
            Quotes from <a href="https://www.officequotes.net">OfficeQuotes.net</a> – View <a href="https://github.com/elysenewland/thats-what-the-office-said">Github</a>
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
    transition: background-color var(--transition-duration) var(--transition-timing);
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