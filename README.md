# Search Bar
A simple search bar component used which can be used for searching on/within the site. A simple hover effect is applied automatically.
An rgba([white || black], .3) is either applied or 'removed' when the effect is in place. The white/black coloring will depend on whether the bar is expanded or not.

## Usage
The search bar component exports only a searchBar component.

### `searchBar` Component
There is one prop which can be used to prevent the collapsing of this search bar component.
- `alwaysExpanded`: By passing this prop as `true` to the component, the search bar will render in its expanded state and remain that way.

There are props available for styling:

- `size`: This is the height of the container. Defaults to 32px.
- `borderColor`: The color assigned here applies to the border of the search bar container. Defaults to black.
- `buttonPrimaryColor`: Defaults to white. The color assigned here applies:
    * Unexpanded- the button background-color
    * Expanded- the button color
- `buttonAltColor`: Defaults to black. The color assigned here applies:
    * Unexpanded- the button color
    * Expanded- the button background-color

