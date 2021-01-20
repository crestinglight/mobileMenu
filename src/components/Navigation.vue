<template>
    <div class="navigation__wrapper">
        <div class="logo">
            <h1>My</h1>
            <h1>Media</h1>
        </div>
        <BurgerIcon />
        <ul id="navigation">
            <li v-for="item in navList" :key="item.title">
                <a href="#">{{ item.title }}</a>
                <ul v-if="item.subcategories" class="sub__menu">
                    <li v-for="subcat in item.subcategories" :key="subcat.title">
                        <a href="#">{{ subcat.title }}</a>
                        <ul v-if="subcat.subcategories" class="sub__menu--tertiary">
                            <li v-for="doubleSubCat in subcat.subcategories" :key="doubleSubCat.title">
                                <a href="#">{{ doubleSubCat.title }}</a>
                            </li>
                        </ul>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</template>

<script>
import BurgerIcon from './BurgerIcon.vue';

export default {
    components: {
        BurgerIcon
    },
    data() {
        return {
            navList: [
                {
                    title: "Games",
                    subcategories: [
                        {
                            title: "PC",
                            subcategories: [
                                {
                                    title: "Darkest Dungeon"
                                },
                                {
                                    title: "League of Legends"
                                },
                                {
                                    title: "Frostpunk"
                                },
                                {
                                    title: "Might & Magic VII"
                                }
                            ]
                        },
                        {
                            title: "PlayStation",
                            subcategories: [
                                {
                                    title: "Horizon Zero Dawn"
                                },
                                {
                                    title: "Red Dead Redemption 2"
                                },
                                {
                                    title: "Skyrim"
                                },
                                {
                                    title: "Spyro Reignited"
                                },
                            ]
                        },
                        {
                            title: "Nintendo Switch",
                            subcategories: [
                                {
                                    title: "A Hat in Time"
                                },
                                {
                                    title: "Untitled Goose Game"
                                },
                                {
                                    title: "Octopath Traveler"
                                },
                            ]
                        },
                        {
                            title: "Indie",
                            subcategories: [
                                {
                                    title: "Disco Elysium"
                                },
                                {
                                    title: "Don't Starve"
                                },
                                {
                                    title: "Hard West"
                                },
                                {
                                    title: "Stardew Valley"
                                }
                            ]
                        }
                    ]
                },
                {
                    title: "Movies",
                    subcategories: [
                        {
                            title: "Action",
                            subcategories: [
                                {
                                    title: "The Dark Knight",
                                },
                                {
                                    title: "John Wick",
                                },
                                {
                                    title: "Leon the Professional",
                                },
                                {
                                    title: "Crouching Tiger, Hidden Dragon"
                                },
                                {
                                    title: "Blade"
                                }
                            ]
                        },
                        {
                            title: "Drama",
                            subcategories: [
                                {
                                    title: "Shawshank Redemption",
                                },
                                {
                                    title: "Parasite",
                                },
                                {
                                    title: "All About Eve",
                                },
                                {
                                    title: "Goodfellas"
                                },
                                {
                                    title: "Whiplash"
                                }
                            ]
                        },
                        {
                            title: "Comedy",
                            subcategories: [
                                {
                                    title: "Monty Python and the Holy Grail",
                                },
                                {
                                    title: "Idiocracy",
                                },
                                {
                                    title: "Blues Brothers",
                                },
                                {
                                    title: "Office Space"
                                }
                            ]
                        },
                        {
                            title: "Horror",
                            subcategories: [
                                {
                                    title: "Train to Busan",
                                },
                                {
                                    title: "Alien",
                                },
                                {
                                    title: "Cube",
                                },
                                {
                                    title: "Saw"
                                }
                            ]
                        },
                        {
                            title: "Best of All Time",
                            subcategories: [
                                {
                                    title: "The Room",
                                },
                                {
                                    title: "Battlefield Earth",
                                },
                                {
                                    title: "Troll 2",
                                },
                                {
                                    title: "Catwoman",
                                },
                            ]
                        },
                    ],
                },
            ]
        }
        
    }
}
</script>

<style scoped>
.navigation__wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
}
.logo {
    position: relative;
    padding: 12px 16px;
    top: -9px;
}
.logo h1 {
    font-family: 'Permanent Marker', cursive;
    font-size: 28px;
}
.logo h1:nth-child(2) {
    position: absolute;
    top: 28px;
    left: 46px;
}
#navigation {
    width: 200px;
    position: absolute;
    top: 54px;
    left: 0;
    background-color: white;
}
</style>
