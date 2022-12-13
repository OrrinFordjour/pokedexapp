<template>
    <div class="bg-white">
        <div class="mx-auto max-w-7xl py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <p class="text-center text-lg font-semibold text-gray-600">
                Trusted by over 5 very average small businesses
            </p>
            <div class="mt-6 grid grid-cols-2 gap-0.5 md:grid-cols-3 lg:mt-8">
                <div v-for="(pokemon, index) in pokemons" :key="`poke-${index}`"
                    class="col-span-1 flex justify-center bg-gray-50 py-8 px-8 text-sm">
                    <img :src="imageUrl + pokemon.id + '.png'" alt="" />
                    <ul>
                        <li class="capitalize">{{ pokemon.name }}</li>
                        <li>{{ pokemon.base_experience }}</li>
                        <li>Milk</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            pokemons: [],
            imageUrl:
                "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/",
            nextUrl: "",
        };
    },
    mounted() {
        fetch("https://pokeapi.co/api/v2/pokemon/")
            .then((res) => res.json())
            .then((data) => {
                this.nextUrl = data.next;
                data.results.forEach((pokemon) => {
                    pokemon.id = pokemon.url
                        .split("/")
                        .filter(function (part) {
                            return !!part;
                        })
                        .pop();
                    this.pokemons.push(pokemon);
                });
            });
    },
};
</script>
