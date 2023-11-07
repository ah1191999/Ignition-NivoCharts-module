# Nivo Chart Component

The Nivo Chart component allows you to create Sankey charts and GitHub calendars in Ignition. This document provides details on how to configure and use this component.

## Sankey Chart

The Sankey Chart is a visual representation of the flow and distribution of resources, values, or quantities between multiple entities or components.

### Properties

| Property                       | Type     | Description                                                                                   | Default   |
| ------------------------------ | -------- | --------------------------------------------------------------------------------------------- | --------- |
| `data`                         | Object   | An object to define the nodes and links properties.                                          | -         |
| - `links`                      | Array    | An array of objects defining connections.                                                   | -         |
|   - `source`                   | String   | Refers to the connection's origin.                                                           | -         |
|   - `target`                   | String   | Points to the connection's destination.                                                      | -         |
|   - `value`                    | Number   | Represents the connection value.                                                             | -         |
|   - `tooltipEmbeddedView`      | Object   | Main properties in a normal EmbeddedView for link tooltips.                                  | -         |
| - `nodes` (Optional)           | Array    | An array of objects for custom styling and data for nodes.                                    | -         |
|   - `id`                       | String   | ID of the node to link.                                                                     | -         |
|   - `nodeColor`                | String   | Custom color for the node (activated when 'nodeStyle.color.customNodeColor' is set to true). | -         |
|   - `nodeBorderColor`           | String   | Custom border color for the node (activated when 'nodeStyle.nodeBorderColor.customNodeBorderColor' is set to true). | - |
|   - `tooltipEmbeddedView`      | Object   | Main properties in a normal EmbeddedView for node tooltips.                                  | -         |
|   - `label` (Optional)         | String   | Display on the chart and legend (set to 'false' to display the 'id').                        | -         |
| `nodeStyle`                    | Object   | Contains node styling properties.                                                            | -         |
| - `nodeThickness`             | Number   | Thickness of the nodes.                                                                     | 30        |
| - `nodeOpacity`               | Number   | Opacity of the nodes (0~1).                                                                | 1         |
| - `nodeHoverOpacity`          | Number   | Opacity of the nodes on hover (0~1).                                                       | 1         |
| - `nodeHoverOthersOpacity`    | Number   | Opacity of other nodes on hover (0~1).                                                     | 0.15      |
| - `nodeSpacing`               | Number   | Spacing between nodes at the same level.                                                   | 20        |
| - `nodeInnerPadding`          | Number   | Inner padding of nodes (distance from links, subtracted from nodeThickness).              | 0         |
| - `nodeBorderWidth`           | Number   | Width of the node border.                                                                   | 1         |
| - `nodeBorderColor`           | Object   | Contains node border color properties.                                                      | -         |
|   - `customNodeBorderColor`    | Boolean  | If true, custom node border color is activated.                                             | false     |
|   - `nodeBorderColorMode`     | Enum     | Method to compute node border color ('inherit' or 'singleBorderColor').                     | 'inherit' |
|   - `modifiers`               | Enum     | Type of modifier for node border color ('brighter', 'darker', 'opacity').                    | 'opacity' |
|   - `value`                   | Number   | Value to apply to the modifiers (0~3).                                                     | 0.6       |
|   - `color`                   | Color    | Color of the node border.                                                                   | -         |
| - `color`                      | Object   | Contains node color properties.                                                              | -         |
|   - `customNodeColor`         | Boolean  | If true, the node color property in the data will be activated.                              | false     |
|   - `colorScheme`             | [See](https://nivo.rocks/guides/colors/) | -                             | -         |
| `linkStyle`                    | Object   | Defines styling options for links.                                                          | -         |
| - `linkOpacity`               | Number   | Link opacity (0~1).                                                                         | 0.25      |
| - `linkHoverOpacity`          | Number   | Link opacity on hover (0~1).                                                                | 0.6       |
| - `linkHoverOthersOpacity`    | Number   | Other links opacity on hover (0~1).                                                         | 0.15      |
| - `linkContract`              | Number   | Determines the contract width of the links.                                                | 0         |
| - `linkBlendMode`            | Enum     | CSS mix-blend-mode for links (e.g., 'multiply').                                             | 'multiply' |
| - `enableLinkGradient`        | Boolean  | Enable gradient from source/target nodes instead of plain color.                             | true      |
| `labelCfg`                     | Object   | Defines label properties.                                                                    | -         |
| - `enableLabels`              | Boolean  | Enable or disable the display of labels.                                                    | true      |
| - `labelPosition`             | Enum     | Position of labels ('inside' or 'outside').                                                 | 'inside'  |
| - `labelPadding`              | Number   | Padding distance of labels from the nodes.                                                  | 9         |
| - `labelOrientation`          | Enum     | Orientation of labels ('horizontal' or 'vertical').                                         | 'horizontal' |
| - `labelTextColor`            | Object   | Defines text color of labels.                                                               | -         |
|   - `labelTextColorMode`      | Enum     | Method to compute the label text color ('inherit' or 'custom').                              | 'inherit' |
|   - `modifiers`               | Enum     | Type of modifier for label text color ('brighter', 'darker', 'opacity').                    | 'darker'  |
|   - `value`                   | Number   | Numeric value within a range of 0 to 3.                                                     | 1.5       |
|   - `color`                   | Color    | Custom color for label text.                                                                | '#000'    |

### Interactivity

| Property                       | Type     | Description                        | Default   |
| ------------------------------ | -------- | ---------------------------------- | --------- |
| `customNodeTooltip`            | Boolean  | Enable custom node tooltips.        | false     |
| `commonNodeTooltipFormat`      | String   | Format for node tooltips.           | '{node.id}' |
| `customLinkTooltip`            | Boolean  | Enable custom link tooltips.        | false     |
| `commonLinkTooltipFormat`      | String   | Format for link tooltips.           | '{link.sourceId}-->{link.targetId}  value:{link.value}' |
| `isInteractive`                | Boolean  | Enable or disable interactivity.    | true      |

### Events

- `onLinkClicked`: Returns an object with link details:
  - `sourceId` (String)
  - `sourceValue` (Number)
  - `targetId` (String)
  - `targetValue` (String)
  - `linkValue` (Number)

- `onNodeClicked`: Returns an object with node details:
  - `nodeId` (String)
  - `nodeValue` (Number)
  - `totalOut` (Number)
  - `totalIn` (Number)
  - `outInfo` (Array of objects, each containing `id` and `value`)
  - `intoInfo` (Array of objects, each containing `id` and `value`)

## Additional Properties

You can refer to the [Nivo Chart documentation](https://nivo.rocks/guides/legends/) for more information on legends and additional properties.

## Styling

The component allows you to style various chart elements using the `chartStyle` property.

## Motion Configuration

The component provides options for controlling transitions and animations with the `motionCfg` property.

For more detailed information on customization and styling, please refer to the [Nivo Chart documentation](https://nivo.rocks/guides/).

