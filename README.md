# Nivo Chart Component

The Nivo Chart component allows you to create Sankey charts and GitHub calendars in Ignition. This document provides details on how to configure and use this component.
<img src="image.png" alt="SankeyChart" width="100%" />

## Sankey Chart

The Sankey Chart is a visual representation of the flow and distribution of resources, values, or quantities between multiple entities or components.

### Properties

#### `data` (Object)

- `links` (Array of Objects)
  - `source` (String): Refers to the connection's origin.
  - `target` (String): Points to the connection's destination.
  - `value` (Number): Represents the connection value.
  - `tooltipEmbeddedView` (Object): Main properties in a normal EmbeddedView that you can attach to the link (activated when 'interactivity.customLinkTooltip' is set to true).

- `nodes` (Array of Objects) [Optional]
  - `id` (String): ID of the node which you want to link.
  - `nodeColor` (String): Custom color for the node (activated when 'nodeStyle.color.customNodeColor' is set to true).
  - `nodeBorderColor` (String): Custom border color for the node (activated when 'nodeStyle.nodeBorderColor.customNodeBorderColor' is set to true).
  - `tooltipEmbeddedView` (Object): Properties in a normal EmbeddedView that you can attach to the node (activated when 'interactivity.customNodeTooltip' is set to true).
  - `label` (String) [Optional]: Optional property to display on the chart and legend. Set to 'false' to display the 'id' instead.

#### `nodeStyle` (Object)

- `nodeThickness` (Number): Thickness of the nodes (default: 30).
- `nodeOpacity` (Number): Opacity of the nodes (0~1) (default: 1).
- `nodeHoverOpacity` (Number): Opacity of the nodes on hover (0~1) (default: 1).
- `nodeHoverOthersOpacity` (Number): Opacity of other nodes on hover (0~1) (default: 0.15).
- `nodeSpacing` (Number): Spacing between nodes at the same level (default: 20).
- `nodeInnerPadding` (Number): Inner padding of nodes, the distance from links, subtracted from nodeThickness (default: 0).
- `nodeBorderWidth` (Number): Width of the node border (default: 1).
- `nodeBorderColor` (Object):
  - `customNodeBorderColor` (Boolean): If true, custom node border color is activated (default: false).
  - `nodeBorderColorMode` (Enum: "inherit", "singleBorderColor"): Method to compute node border color (default: "inherit").
  - `modifiers` (String, Enum: "brighter", "darker", "opacity"): Type of modifier for node border color (default: "opacity").
  - `value` (Number): Value to apply to the modifiers (0~3).
  - `color` (String, Format: Color): Color of the node border.

- `color` (Object):
  - `customNodeColor` (Boolean): If true, the node color property in the data will be activated.
  - `colorScheme` (See [here](https://nivo.rocks/guides/colors/)).

#### `linkStyle` (Object)

- `linkOpacity` (Number): Link opacity (0~1) (default: 0.25).
- `linkHoverOpacity` (Number): Link opacity on hover (0~1) (default: 0.6).
- `linkHoverOthersOpacity` (Number): Other links opacity on hover (0~1) (default: 0.15).
- `linkContract` (Number): Determines the contract width of the links (default: 0).
- `linkBlendMode` (String, Enum: "normal", "multiply", ...): Define CSS mix-blend-mode for links (default: "multiply").
  - More info: [MDN Documentation](https://developer.mozilla.org/fr/docs/Web/CSS/mix-blend-mode)
- `enableLinkGradient` (Boolean): Enable/disable gradient from source/target nodes instead of plain color.

#### `labelCfg` (Object)

- `enableLabels` (Boolean): Enable or disable the display of labels (default: true).
- `labelPosition` (Enum: "inside", "outside"): Position of labels (default: "inside").
- `labelPadding` (Number): Padding distance of labels from the nodes (default: 9).
- `labelOrientation` (Enum: "horizontal", "vertical"): Orientation of labels (default: "horizontal").
- `labelTextColor` (Object):
  - `labelTextColorMode` (Enum: "inherit", "custom"): Method to compute the label text color (default: "inherit").
  - `modifiers` (Enum: "brighter", "darker", "opacity"): Adjust text color (default: "darker").
  - `value` (Number): Numeric value within a range of 0 to 3 (default: 1.5).
  - `color` (String, Format: Color): Custom color for label text.

### Interactivity

#### `customNodeTooltip` (Boolean)

When enabled, custom node tooltips are used.

- `commonNodeTooltipFormat` (String): Format for node tooltips (applicable when "customNodeTooltip" is true). Available variables: {node.id}, {node.value}.

#### `customLinkTooltip` (Boolean)

When enabled, custom link tooltips are used.

- `commonLinkTooltipFormat` (String): Format for link tooltips (applicable when "customLinkTooltip" is true). Available variables: {link.sourceId}, {link.targetId}, {link.value}, {link.sourceValue}, {link.targetValue}.

<img src="SankeyChart.gif" alt="SankeyChart" width="100%" />

#### `isInteractive` (Boolean)

Determines whether interactivity is enabled for the chart (default: true).

## Events

- `onLinkClicked` (Function):
  Returns an object with the following properties:
  - `sourceId` (String)
  - `sourceValue` (Number)
  - `targetId` (String)
  - `targetValue` (String)
  - `linkValue` (Number)

- `onNodeClicked` (Function):
  Returns an object with the following properties:
  - `nodeId` (String)
  - `nodeValue` (Number)
  - `totalOut` (Number)
  - `totalIn` (Number)
  - `outInfo` (Array of Objects) (Each object contains `id` and `value` properties)
  - `intoInfo` (Array of Objects) (Each object contains `id` and `value` properties)

## Legends

For information on customizing legends, see the [Nivo Chart Legends Guide](https://nivo.rocks/guides/legends/).

# GitHub Calendar Component

The GitHub Calendar component allows you to create a calendar heatmap representation of data over time in Ignition. This document provides details on how to configure and use this component.

## Properties

#### `data` (Object)

  - `day` (String): Represents the date in "YYYY-MM-DD" format.
  - `value` (Number): Specifies the value for the corresponding date.

- `from` (String)

  - `default`: "2015"
  - `description`: The start date of the chart data.

- `to` (String)

  - `default`: "2017"
  - `description`: The end date of the chart data.


#### `yearCfg` (Object)
  
  - `yearSpacing` (Number)
    - `default`: 40
    - `description`: Specifies the spacing between years in the year view.

  - `yearLegendPosition` (String)
    - `enum`: "before", "after"
    - `default`: "before"
    - `description`: Defines the position of the year legend relative to the year view.

  - `yearLegendOffset` (Number)
    - `default`: 10
    - `description`: Determines the offset between the year legend and the year view.

#### `monthCfg` (Object)

  - `translateTo` (String)
    - `enum`: "en", "es", "fr", "de", "ar", "cn", "none"
    - `default`: "en"
    - `description`: Specifies the language for translating month names.

  - `monthBorderColor` (String)
    - `format`: Color
    - `default`: "#fff"
    - `description`: Sets the color of the border around individual months in the month view.

  - `monthBorderWidth` (Number)
    - `default`: 1
    - `description`: Controls the width of the border around individual months.

  - `monthLegendOffset` (Number)
    - `default`: 10
    - `description`: Determines the offset between the month legend and the month view.

  - `monthLegendPosition` (String)
    - `enum`: "before", "after"
    - `default`: "before"
    - `description`: Defines the position of the month legend relative to the month view.

  - `monthSpacing` (Number)
    - `default`: 3
    - `description`: Specifies the spacing between individual months in the month view.

#### `dayCfg` (Object)

  - `dayBorderColor` (String)
    - `format`: Color
    - `default`: "#0000003D"
    - `description`: Sets the color of the border around individual days in the day view.

  - `dayBorderWidth` (Number)
    - `default`: 1
    - `description`: Controls the width of the border around individual days.

  - `daySpacing` (Number)
    - `default`: 1
    - `description`: Specifies the spacing between individual days in the day view.

#### `chartCfg` (Object)

  - `minValue`
    - `default`: "auto"
    - `description`: Sets the minimum value for the chart.

  - `maxValue`
    - `default`: "auto"
    - `description`: Sets the maximum value for the chart.

  - `legendFormat` (String)
    - `default`: "{data.value} hr"
    - `description`: Defines the format for legends within the chart.

#### `chartStyle` (Object))

  - `colors` (Array of Strings)
    - `default`: ["#97e3d5", "#61cdbb", "#e8c1a0", "#f47560"]
    - `description`: Specifies an array of color values to define the colors used in the chart.

  - `emptyColor` (String)
    - `format`: Color
    - `default`: "#eeeeee"
    - `description`: Sets the color used for empty or unassigned areas in the chart.

  - `direction` (String)
    - `enum`: "horizontal", "vertical"
    - `default`: "horizontal"
    - `description`: Defines the orientation of the chart.

  - `margin` (Object)
    - `description`: Specifies the margin or padding around the chart.

  - `align` (String)
    - `enum`: "top-left", "top-right", "top", "right", "left", "center", "bottom-left", "bottom-right", "bottom"
    - `default`: "center"
    - `description`: Determines the alignment of the chart within its container.

  - `theme` (Object)
    - `description`: Styling configuration for various chart elements.

#### `tooltipCfg` (Object)

  - `isInteractive`
    - `default`: true
    - `description`: Specifies whether the tooltip is interactive.

  - `tooltipMode`
    - `default`: "default"
    - `enum`: "default", "embeddedView", "custom"
    - `description`: Sets the mode for displaying tooltips.

  - `customTooltip` (String)
    - `default`: "{data.day}:{data.value}"
    - `description`: Custom tooltip template with placeholders.

  - `tooltipEmbeddedView` (Object)
    - `path` (String)
    - `useDefaultViewWidth` (Boolean)
    - `useDefaultViewHeight` (Boolean)

## Events

The GitHub Calendar component supports the following events:

- `onClick`
- `onMouseEnter`
- `onMouseLeave`
- `onMouseMove`

All of these events return an object with data like this in normal mode: {"day": "2015-07-09", "value": 66}.

You can customize and configure the component using these properties, and utilize the events to enhance the interactivity of your GitHub Calendar chart in Ignition.

Feel free to add any custom parameters to enhance your embedded view and chart styling based on your specific needs.

