<template>
    <div class="navigation__wrapper">
        <div class="logo">
            <h1>My</h1>
            <h1>Media</h1>
        </div>
        <BurgerIcon v-on:click.native="menuToggle" />
        <div class="nav__wrap">
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
    </div>
</template>

<script>
import BurgerIcon from './BurgerIcon.vue';
import gsap from "gsap";

export default {
    components: {
        BurgerIcon
    },
    methods: {
        menuToggle: function () {
            if(this.menuOpen === false){
                gsap.fromTo(".nav__wrap", 
                    {scaleX: 0.001, scaleY: 0},
                    {
                    ease: "power1.out",
                    duration: 0.3,
                    scaleY: 1
                })
                gsap.fromTo(".nav__wrap", 
                    {scaleX: 0.001, scaleY: 1},
                    {
                    ease: "power2.out",
                    duration: 0.8,
                    delay: 0.3,
                    scaleX: 1
                })
            }else{
                gsap.fromTo(".nav__wrap", 
                    {scaleX: 1, scaleY: 1},
                    {
                    ease: "power2.in",
                    duration: 0.5,
                    scaleX: 0.001
                })
                gsap.fromTo(".nav__wrap", 
                    {scaleX: 0.001, scaleY: 1},
                    {
                    ease: "power2.out",
                    duration: 0.2,
                    delay: 0.5,
                    scaleY: 0
                })
            }
            this.menuOpen = !this.menuOpen;
            console.log("Menu Open: "+this.menuOpen);
        }
    },
    data() {
        return {
            menuOpen: false,
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
                {
                    title: "Books",
                    subcategories: [
                        {
                            title: "Classic",
                            subcategories: [
                                {
                                    title: "1984",
                                },
                                {
                                    title: "Lord of the Flies",
                                },
                                {
                                    title: "Pride and Prejudice",
                                },
                                {
                                    title: "Great Expectations"
                                },
                                {
                                    title: "The Wind in the Willows"
                                }
                            ]
                        },
                        {
                            title: "Sci-Fi and Fantasy",
                            subcategories: [
                                {
                                    title: "Dune",
                                },
                                {
                                    title: "Lord of the Rings",
                                },
                                {
                                    title: "I Have no Mouth and I Must Scream",
                                },
                                {
                                    title: "The Time Machine"
                                },
                                {
                                    title: "Fahrenheit 451"
                                }
                            ]
                        },
                        {
                            title: "Horror",
                            subcategories: [
                                {
                                    title: "Hell House",
                                },
                                {
                                    title: "The Turning of the Screw",
                                },
                                {
                                    title: "Dracula",
                                },
                                {
                                    title: "The Picture of Dorian Gray"
                                },
                                {
                                    title: "Something Wicked This Way Comes"
                                }
                            ]
                        },
                        {
                            title: "European",
                            subcategories: [
                                {
                                    title: "Crime and Punishment",
                                },
                                {
                                    title: "The Metamorphosis",
                                },
                                {
                                    title: "Don Quixote",
                                },
                                {
                                    title: "Robinson Crusoe"
                                }
                            ]
                        },
                    ],
                },
                {
                    title: "Music",
                    subcategories: [
                        {
                            title: "Classic Rock",
                            subcategories: [
                                {
                                    title: "Stevie Ray Vaughan",
                                },
                                {
                                    title: "Bob Segar",
                                },
                                {
                                    title: "Stevie Wonder",
                                },
                                {
                                    title: "King Crimson"
                                },
                                {
                                    title: "Billy Idol"
                                }
                            ]
                        },
                        {
                            title: "90's Rock",
                            subcategories: [
                                {
                                    title: "Pearl Jam",
                                },
                                {
                                    title: "Alice in Chains",
                                },
                                {
                                    title: "Foo Fighters",
                                },
                                {
                                    title: "Stone Temple Pilots"
                                },
                                {
                                    title: "Jane's Addiction"
                                }
                            ]
                        },
                        {
                            title: "Metal",
                            subcategories: [
                                {
                                    title: "Jinjer",
                                },
                                {
                                    title: "Mastodon",
                                },
                                {
                                    title: "Tool",
                                },
                                {
                                    title: "Spiritbox"
                                },
                                {
                                    title: "Within the Ruins"
                                }
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
.nav__wrap {
    width: 100%;
    height: calc(100vh - 64px);
    position: absolute;
    top: 64px;
    left: 0;
    background-color: white;
    transform-origin: top center;
    overflow: hidden;
    transform: scale(0.001, 0);
}
.sub__menu, sub__menu--tertiary {
    max-height: 0;
    overflow: hidden;
}
</style>
