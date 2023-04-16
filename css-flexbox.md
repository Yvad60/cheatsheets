# CSS Flexbox cheatsheet

## Flexbox

A one-dimensional layout system used that provides a way to align and distribute space among items in a container

### Terminology

- **Flex container**: the parent element that contains items
- **Flex items**: direct children of the flex parent container
- **Main axis**: the primary axis by which flex children are placed. It depends on the `flex-direction` property. For example, if `flex-direction: row` is set, then the main axis runs horizontally from left to right.
- **Cross axis**: the opposite axis of the `main axis` when `flex-direction: column` the cross axis is holizontal because the main axis would be vertical.
- **main size**: the flex item's main size can the height or width depending which on the main axis. when `flex-direction: row` is set then the main axis is horizontal and item with will be the one to determine it's main size
- **cros size**: the flex item's main size can the height or width depending which on the cross axis.

