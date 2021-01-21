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
                    <a href="#" class="link__main" v-on:click="dropdownOpen">
                        <span class="link__main--anim">{{ item.title }}</span>
                        <svg class="link__main--anim" width="8px" viewBox="0 0 102 136" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                <g fill="#51007A">
                                    <polygon points="101.941125 68 33.9411255 136 0 136 68 68 0 0 33.9411255 0"></polygon>
                                </g>
                            </g>
                        </svg>
                    </a>
                    <div class="divider"></div>
                    <ul v-if="item.subcategories" class="sub__menu">
                        <div class="sub__header">
                            <h3>{{ item.title }}</h3>
                            <button v-on:click="dropdownClose">
                                <svg width="14px" height="15px" viewBox="0 0 14 15">
                                    <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                        <g fill="#51007A" fill-rule="nonzero">
                                            <path d="M7,6.08578644 L12.3033009,0.782485579 C12.6938252,0.391961287 13.3269901,0.391961287 13.7175144,0.782485579 C14.1080387,1.17300987 14.1080387,1.80617485 13.7175144,2.19669914 L8.41421356,7.5 L13.7175144,12.8033009 C14.1080387,13.1938252 14.1080387,13.8269901 13.7175144,14.2175144 C13.3269901,14.6080387 12.6938252,14.6080387 12.3033009,14.2175144 L7,8.91421356 L1.69669914,14.2175144 C1.30617485,14.6080387 0.67300987,14.6080387 0.282485579,14.2175144 C-0.108038713,13.8269901 -0.108038713,13.1938252 0.282485579,12.8033009 L5.58578644,7.5 L0.282485579,2.19669914 C-0.108038713,1.80617485 -0.108038713,1.17300987 0.282485579,0.782485579 C0.67300987,0.391961287 1.30617485,0.391961287 1.69669914,0.782485579 L7,6.08578644 Z"></path>
                                        </g>
                                    </g>
                                </svg>
                            </button>
                        </div>
                        <li v-for="subcat in item.subcategories" :key="subcat.title">
                            <a href="#" v-on:click="dropdownToggle">
                                <span>{{ subcat.title }}</span>
                                <svg class="svg__down" width="8px" viewBox="0 0 102 136" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                    <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                        <g fill="#fff">
                                            <polygon points="101.941125 68 33.9411255 136 0 136 68 68 0 0 33.9411255 0"></polygon>
                                        </g>
                                    </g>
                                </svg>
                            </a>
                            <ul v-if="subcat.subcategories" class="sub__menu--tertiary">
                                <li v-for="doubleSubCat in subcat.subcategories" :key="doubleSubCat.title">
                                    <a href="#">
                                        <div class="arrow__highlight">
                                            <svg width="8px" viewBox="0 0 102 136" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                                <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                                    <g fill="#fff">
                                                        <polygon points="101.941125 68 33.9411255 136 0 136 68 68 0 0 33.9411255 0"></polygon>
                                                    </g>
                                                </g>
                                            </svg>
                                        </div>
                                        <span>{{ doubleSubCat.title }}</span>
                                    </a>
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
                gsap.to(".lettuce", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    y: 12,
                })
                gsap.to(".lettuce", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    delay: 0.35,
                    rotation: -45,
                    skewX: 45,
                    y: 10
                })
                gsap.to(".tomato", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    delay: 0.35,
                    rotation: -45,
                    skewX: 45,
                    y: -2
                })
                gsap.to(".bacon", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    delay: 0.35,
                    rotation: 45,
                    skewX: -45,
                    x: 6,
                    y: 1.74
                })
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
                gsap.to(".lettuce", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    rotation: 0,
                    skewX: 38,
                    y: 12
                })
                gsap.to(".tomato", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    rotation: 0,
                    skewX: 38,
                    y: 0
                })
                gsap.to(".bacon", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    rotation: 0,
                    skewX: 38,
                    x: 0,
                    y: 0
                })
                gsap.to(".lettuce", 
                    {
                    ease: "power2.in",
                    duration: 0.3,
                    delay: 0.5,
                    y: 0,
                })
                gsap.to(".link__main--anim", 
                    {
                    stagger: 0.01,
                    ease: "power2.in",
                    duration: 0.1,
                    x: -15,
                    y: -15,
                    opacity: 0
                })
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
        },
        dropdownOpen: function (event) {
            event.preventDefault();
            let dropdownLink = event.currentTarget;
            let list = dropdownLink.nextSibling.nextSibling;
            list.classList.add("open");
        },
        dropdownClose: function (event) {
            event.preventDefault();
            let buttonPressed = event.currentTarget;
            let list = buttonPressed.parentElement.parentElement;
            let subs = document.getElementsByClassName("sub__menu--tertiary");
            for (let i = 0; i < subs.length; i++) {
                subs[i].classList.remove("open");
            }
            list.classList.remove("open");
        },
        dropdownToggle: function (event) {
            event.preventDefault();
            let subnavLink = event.currentTarget;
            let sublist = subnavLink.nextSibling;
            subnavLink.classList.toggle("svg__up");
            sublist.classList.toggle("open");
        }
    },
    mounted(){
    },
    data() {
        return {
            menuOpen: false,
            currTitle: "Home",
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
.sub__header {
    position: relative;
}
.sub__header button {
    background-color: white;
    position: absolute;
    top: 0;
    right: 0;
    height: 100%;
    padding: 0 24px;
}
ul#navigation {
    position: relative;
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
.sub__menu {
    overflow: auto;
    position: absolute;
    top: 0;
    left: 100%;
    z-index: 300;
    width: 80%;
    min-height: calc(100vh - 126px);
    max-height: calc(100vh - 126px);
    background-color: #E70941;
    transition: 0.2s all ease-in;
} 
.sub__menu.open {
    left: 20%;
}
.sub__menu h3 {
    background-color: #51007A;
    color: white;
    font-family: 'Cabin', Arial, sans-serif;
    font-size: 22px; 
    padding: 24px 16px;
}
ul#navigation li .sub__menu > li a {
    font-family: 'Overpass', Helvetica, sans-serif;
    font-weight: 600;
    color: white;
    border-bottom: 3px solid white;
}
.sub__menu--tertiary {
    max-height: 0px;
    overflow: hidden;
    transition: 0.3s all ease;
    background-color: white;
}
.sub__menu--tertiary.open {
    max-height: 1000px;
}
ul#navigation li .sub__menu--tertiary li {
    border-bottom: 2px solid #51007A;
}
ul#navigation li .sub__menu--tertiary li a {
    position: relative;
    display: block;
    font-family: 'Overpass', Helvetica, sans-serif;
    font-size: 14px;
    line-height: 18px;
    font-weight: 400;
    color: #51007A;
    padding: 16px 54px;
    border: none;
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
    font-family: 'Overpass', Helvetica, sans-serif;
    margin: 0 16px;
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
.svg__down {
    transform: rotate(90deg);
    transition: 0.3s all ease;
}
.svg__up .svg__down {
    transform: rotate(-90deg);
}
.arrow__highlight {
    background-color: #51007A;
    height: 100%;
    padding: 0 16px;
    position: absolute;
    top: 0;
    left: 0;
    border-bottom: 2px solid white;
}
.arrow__highlight svg {
    margin: 18px 0;
}
</style>
