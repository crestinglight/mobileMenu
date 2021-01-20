<template>
    <div class="navigation__wrapper">
        <div class="logo">
            <h1>My</h1>
            <h1>Media</h1>
        </div>
        <BurgerIcon v-on:click.native="menuToggle" />
        <div class="nav__wrap">
            <div class="hello__wrap">
                <div class="hello">
                    <h2>Hey there Indigo Slate</h2>
                </div>
            </div>
            <ul id="navigation">
                <li v-for="item in navList" :key="item.title">
                    <a href="#" class="link__main">
                        <span class="link__main--anim">{{ item.title }}</span>
                        <svg class="link__main--anim" width="8px" height="auto" viewBox="0 0 102 136" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                <g id="Artboard" fill="#51007A">
                                    <polygon id="Combined-Shape" points="101.941125 68 33.9411255 136 0 136 68 68 0 0 33.9411255 0"></polygon>
                                </g>
                            </g>
                        </svg>
                    </a>
                    <div class="divider"></div>
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
                    duration: 0.7,
                    delay: 0.3,
                    scaleX: 1
                })
                gsap.fromTo(".link__main--anim", 
                    {opacity: 0, x: -15, y: -15},
                    {
                    stagger: 0.1,
                    ease: "power2.out",
                    duration: 0.8,
                    delay: 1,
                    x: 0,
                    y: 0,
                    opacity: 1
                })
                gsap.fromTo(".divider", 
                    {x: "-100vw"},
                    {
                    stagger: 0.1,
                    ease: "power2.out",
                    duration: 0.8,
                    delay: 0.8,
                    x: 0
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
.hello__wrap {
    background-color: #E70941;
    color: white;
    font-family: 'Overpass', Helvetica, sans-serif;
    font-size: 16px;
    background-image: linear-gradient(to top left, #51007A, #E70941);
}
.hello {
    padding: 12px 0px 32px;
    display: block;
    width: 100%;
    background-image: url('../assets/brushstrokes.png');
    background-repeat: no-repeat;
    background-position: 50vw 50%;
    background-size: auto 250%;
}
.hello h2 {
    margin: 0 16px;
}
ul#navigation > li a {
    font-family: 'Cabin', Arial, sans-serif;
    font-weight: 700;
    font-size: 24px;
    text-decoration: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 22px 16px;
    transition: 0.2s color ease-in;
}
ul#navigation > li a:hover {
    color: #E70941;
}
ul#navigation > li a:hover + .divider {
    background-color: #E70941;
}
.divider {
    height: 3px;
    display: block;
    position: relative;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: #51007A;
    transform: translateX(-100vw);
    transition: 0.2s background-color ease-in;
}
</style>
