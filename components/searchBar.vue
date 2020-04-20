<template>
    <div class="search-bar__flex-container"><div class='search-bar'>
    <input
    type="text"
    class="search-bar__input"
    placeholder="Search"
    aria-label="search"
    />
    <button class="search-bar__button" role='button'>
    <q-icon name='search' class='search-bar__icon'></q-icon>
    </button>
    </div></div>
</template>

<script>
export default {
    name: 'searchBar'
}
</script>

<style lang='scss' scoped>
    .search-bar__flex-container {
        display:flex;
        justify-content: inherit;
        flex:1;
    }
    .search-bar {
        --size: 30px;

        border: 2px solid black;
        display: flex;
        margin: .5em;
        border-radius: calc(var(--size));
        height: var(--size);
        width: var(--size);
        flex: 0;
        flex-basis: initial;
        position:relative;
        //transition: width 300ms cubic-bezier(0.18, 0.89, 0.32, 1.08);
        transition: flex 300ms cubic-bezier(0.18, 0.89, 0.32, 1.08);
        z-index: 9;

        &__input {
            margin-left: auto;
            flex-grow: 1;
            font-size: 1.5em;
            border: none;
            padding: 0 .5em;
            overflow: hidden;
            position:absolute;
            line-height: 1;
            cursor: pointer;
            background-color:rgba(0,0,0,.0);
            opacity: 0;
            width: calc(100% - var(--size));
            z-index: -1;
            border-radius: calc(var(--size));
        }

        &__button {
            --font-size: 1em;
            font-size: var(--font-size);
            border-radius: 50%;
            margin-left:auto;
            height: calc(var(--size) - 10px);
            width: calc(var(--size) - 10px);
            border: none;
            background:transparent;
            background-color:white;
            transition: margin-left 300ms ease-in-out;

            margin-top:auto;
            margin-bottom: auto;
            margin-right:3px;
            justify-content: center;
            align-content:center;
            vertical-align: middle;
            text-align: center;
            position:relative;
            //padding: calc(var(--font-size) / var(--font-size));
        }

        &__icon {
            //display:block;
            position:absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            // vertical-align: middle;
            // justify-content: center;
            // text-align: center;
            // height:var(--size);
            // width:var(--size);
            //height: 100%;
            //width:  100%;
            //padding: 10px;
            //padding-right: calc(var(--size) / 1em)
        }

        &:focus-within {
            flex: 1;
            background-color: white;

            .search-bar__input {
                opacity: 1;
                background-color: white;
                cursor: initial;

            }
            .search-bar__button {
                background-color: black;
                color: white;
            }
        }
    }
</style>
