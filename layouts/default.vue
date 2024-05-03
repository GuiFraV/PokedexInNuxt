<template>
    <div>
        <nav>
            <nuxt-link to="/">🏠 - Home</nuxt-link> |
            <nuxt-link to="/search">🔍 - Search</nuxt-link>
        </nav>
        <slot />
    </div>
</template>

<style>

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}


nav {
    background: #333;
    padding: 10px;
    color: white;
    text-align: center;
}

nav a {
    color: white;
    margin: 0 10px;
    text-decoration: none;
    transition: color 0.3s;
}

nav a:hover {
    color: lightblue;
    transition: color 0.3s;
}

</style>