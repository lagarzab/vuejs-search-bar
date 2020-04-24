<template>
    <div class="search-bar__flex-container">
        <div :class='"search-bar " + forceExpandClass' :style='searchBarStyle'>
            <input
                type="text"
                class="search-bar__input"
                placeholder="Search"
                aria-label="search"
            />
            <button
                class="search-bar__button"
                :style='buttonStyle'
                role='button'
            >
                <div class='search-bar__hover-layer'>
                    <q-icon
                        name='search'
                        class='search-bar__icon'
                    ></q-icon>
                </div>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'searchBar',
    data () {
        return {
            searchBarStyle: '',
            buttonStyle: '',
            forceExpandClass: ''
        }
    },
    props: {
        size: {
            type: String,
            default: '32px'
        },
        borderColor: {
            type: String,
            default: ''
        },
        buttonPrimaryColor: {
            type: String,
            default: ''
        },
        buttonAltColor: {
            type: String,
            default: ''
        },
        alwaysExpanded: {
            type: Boolean,
            default: false
        }
    },
    created () {
        document.documentElement.style.setProperty('--search-bar-size', '32px')
        document.documentElement.style.setProperty('--border-color:','#000')
        document.documentElement.style.setProperty('--button-pri-color','#fff')
        document.documentElement.style.setProperty('--button-alt-color','#000')
    },
    mounted () {
        let primaryColor = this.buttonPrimaryColor ? this.buttonPrimaryColor : '#fff'
        let altColor = this.buttonAltColor ? this.buttonAltColor : '#000'
        let borderColor = this.borderColor ? this.borderColor : altColor
        this.forceExpandClass = this.alwaysExpanded ? 'forceExpand' : ''

        this.searchBarStyle = `--search-bar-size:${this.size};`;
        this.searchBarStyle += `--border-color:${borderColor};`
        this.buttonStyle = `--button-pri-color:${primaryColor};`
        this.buttonStyle += `--button-alt-color:${altColor};`
    }
}
</script>

<style lang='scss'>
    .search-bar__flex-container {
        display:flex;
        justify-content: inherit;
        flex:1;
    }
    .search-bar {
        --font-size: max(1.25rem, calc(var(--search-bar-size) / 1.6));

        border: 2px solid var(--border-color);
        display: flex;
        margin: .5em;
        border-radius: var(--search-bar-size);
        height: var(--search-bar-size);
        width: var(--search-bar-size);
        flex: 0;
        flex-basis: initial;
        position:relative;
        transition: flex 300ms cubic-bezier(0.18, 0.89, 0.32, 1.08);
        z-index: 0;

        &__input {
            margin-left: auto;
            flex-grow: 1;
            font-size: var(--font-size);
            border: none;
            padding: 0 .5em;
            overflow: hidden;
            position:absolute;
            height:100%;
            width: 100%;
            line-height: 1;
            cursor: pointer;
            opacity: 0;
            z-index: 2;
            border-radius: var(--search-bar-size);
        }

        &.forceExpand {
            flex: 1;
            & .search-bar__input {
                opacity: 1;
                background-color: white;
                cursor: initial;
                padding-right: var(--search-bar-size);
                z-index: 1;
            }

            .search-bar__button {
                background-color: var(--button-alt-color);
                color: var(--button-pri-color);
                z-index: 2;
            }

            & .search-bar__button:hover .search-bar__hover-layer {
                background-color: rgba(white, .3);
            }
        }

        &__button {
            position:relative;
            font-size: var(--font-size);
            border-radius: 50%;
            height: calc(var(--search-bar-size) - 10px);
            width: calc(var(--search-bar-size) - 10px);
            border: none;
            margin-left:auto;
            margin-top:auto;
            margin-bottom: auto;
            margin-right:3px;
            background-color: var(--button-pri-color);
            color: var(--button-alt-color);
            transition: background-color 200ms ease-in-out;
        }

        &__icon {
            position:absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        &__hover-layer {
            position: absolute;
            left:0;
            right: 0;
            top: 0;
            bottom: 0;
            border-radius: 50%;
            z-index: 1;
        }

        &:not(.forceExpand) &__input:hover {
            &:not(:focus-within) ~ button .search-bar__hover-layer {
                background-color: rgba(black, .3);
            }
        }

        &:not(.forceExpand):focus-within {
            flex: 1;

            .search-bar__input {
                opacity: 1;
                background-color: white;
                cursor: initial;
                padding-right: var(--search-bar-size);

            }

            .search-bar__button {
                background-color: var(--button-alt-color);
                color: var(--button-pri-color);
                z-index: 2;
            }

            & .search-bar__button:hover .search-bar__hover-layer {
                background-color: rgba(white, .3)
            }
        }
    }
</style>
