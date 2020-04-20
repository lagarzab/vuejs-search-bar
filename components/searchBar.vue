<template>
    <div class="search-bar__flex-container">
        <div class='search-bar' :style='style'>
            <input
                type="text"
                class="search-bar__input"
                placeholder="Search"
                aria-label="search"
            />
            <button class="search-bar__button" role='button'>
            <q-icon name='search' class='search-bar__icon'></q-icon>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'searchBar',
    data () {
        return {
            style: ''
        }
    },
    props: {
        size: {
            type: String,
            default: '32px'
        },
    },
    created () {
        document.documentElement.style.setProperty('--search-bar-size', '32px')
    },
    mounted () {
        this.style = '--search-bar-size: ' + this.size + ';';
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

        border: 2px solid black;
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
            background-color:rgba(0,0,0,1);
            opacity: 0;
            z-index: 1;
            border-radius: var(--search-bar-size);
        }

        &__button {
            position:relative;
            font-size: var(--font-size);
            border-radius: 50%;
            height: calc(var(--search-bar-size) - 10px);
            width: calc(var(--search-bar-size) - 10px);
            border: none;
            background-color:white;
            margin-left:auto;
            margin-top:auto;
            margin-bottom: auto;
            margin-right:3px;
            z-index: -1;
            transition: background-color 200ms ease-in-out;
        }

        &__icon {
            position:absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        &:focus-within {
            flex: 1;
            background-color: white;

            .search-bar__input {
                opacity: 1;
                background-color: white;
                cursor: initial;
                padding-right: var(--search-bar-size);

            }
            .search-bar__button {
                background-color: black;
                color: white;
                z-index: 2;
            }
        }
    }
</style>
