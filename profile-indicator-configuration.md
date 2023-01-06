# Profile Indicator Configuration

Each ProfileIndicator can be individually configured in the Admin backend using a json dictionary. A typical configuration might look as follows:

```
{
    "types": {
        "Value": {"formatting": "~s", "minX": 0, "maxX": 5000},
        "Percentage": {"formatting": ".0%", "minX": 0, maxX: 100}
    },
    "disableToggle": false,
    "defaultType": "Percentage",
    "xTicks": 2,
    "filter": {
        "defaults": [
            {
                "name": "income sources",
                "value": "Locally generated(%)"
            }
        ]
    },
}
```

All values are optional. Below is a description of each configuration option:

`formatting`: How numbers are formatting on the graph. A description of the specification used can be found here: [https://github.com/d3/d3-format](https://github.com/d3/d3-format). The default formatting for `Value`is `~s` and `.0%` for `Percentage`.

`minX`: minimum value on the x-axis. This defaults to `0`.

`maxX`: maximum value on the x-axis. This defaults to the maximum value in the data.

`disableToggle`: By default, graphs can be toggled to display both a percentage and a value view. Setting this value to false removes that toggle from the chart context (hamburger) menu. The toggle is enabled by default.

`defaultType`: Sets whether the toggle defaults to Percentage or Value. If `disableToggle` is set to false, then this is the only visible view. The Percentage view is set as default.

`xTicks` : Sets the number of ticks on the X-Axis.

### Default filters

Filter options are available for any dimensions other than the indicator variable.

To specify that a filter must be applied automatically without user interaction, default filters can be specified.

To do so, add an object with keys `name` and `value` to the `filter.defaults` array.

* `name` should be the subindicator group name
* `value` should be the value that should be selected by default.

e.g. to ensure that "Locally generated(%)" is matched on the "income sources" column, add the following configuration to the profile indicator:

```
    "filter": {
        "defaults": [
            {
                "name": "income sources",
                "value": "Locally generated(%)"
            }
        ]
    },
```

### Excluding profile indicators

It is possible to hide profile indicators in data mapper using the `exclude`  property.`exclude` is optional. If a profile indicator does not have this property, it will not be excluded.

```
  "exclude": [
    "data mapper"
  ]
```

### Setting the chart type

At the moment we support 2 chart types : bar chart and line chart.  `chartType` can be set as `line` for line charts or`bar` for bar charts. If `chartType` is not set, the default is the bar chart

```
 "chartType": "line" 
```

## Examples

#### Value only, formatted as percentage

For pre-calculated percentages, usually with absolute choropleth method.

```
{
    "types": {
        "Value": {"formatting": "~.1%"}
    },
    "disableToggle": true,
    "defaultType": "Value"
}
```

#### Values formatted as whole numbers with comma thousand separator

Ideal for population data, were you would like a thousand separator and whole numbers.

```
{
  "types": {
    "Value": {
      "formatting": ",.0f"
    }
  }
}
```
