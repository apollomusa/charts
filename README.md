# Chart Libraries

* [Plottable (Palantir)](#plottable-palantir)
* [Victory (FormidableLabs)](#victory-formidablelabs)
* [react-vis (Uber)](#react-vis-uber)
* [Recharts](#recharts)

---

## Plottable (Palantir)

[Demo/Code](https://codesandbox.io/s/31krw1zymq)

##### Description:

> Plottable's core philosophy is "Composition over Configuration", so a lot of the API flexibility is in choosing which Components to use, and how to arrange them in Tables, rather than setting high-level properties on the charts.

| Licence | Downlods (weekly) | Github stars | Github (Avg time to resolve an issue) | React components | TypeScript support |
| :-----: | ----------------: | -----------: | ------------------------------------: | ---------------- | ------------------ |
|   MIT   |               565 |         2406 |                                  67 d | No               | Yes                |

##### Customizable/Extensible:

* No support for theming
* Not much documentation on customizing the appearance of the charts
* Specific charts with data displayed in a gradient expose an API to configure the colours `colorScale.range`
* Did not see APIs exposing sizing
* Requires targeting the selectors:

```css
.plottable .guide-line-layer.red .content line.guide-line {
  stroke: #ff0000;
}
```

##### Dependencies: (8)

* @types/d3
* @types/is-plain-object
* d3
* d3-ease
* d3-shape
* is-plain-object
* tslib
* typesettable

##### Browser support:

* Chrome
* Firefox
* Internet Explorer 9 and later
* Safari (desktop and mobile

##### Documentation:

* Palantir style documentation, includes code, example, and APIs

##### Example code block:

```javascript
var scale = new Plottable.Scales.Linear();
var colorScale = new Plottable.Scales.InterpolatedColor();
colorScale.range(["#BDCEF0", "#5279C7"]);
var data = [
  { val: 1 },
  { val: 2 },
  { val: 3 },
  { val: 4 },
  { val: 5 },
  { val: 6 }
];

var plot = new Plottable.Plots.Pie()
  .addDataset(new Plottable.Dataset(data))
  .sectorValue(function(d) {
    return d.val;
  }, scale)
  .innerRadius(90)
  .attr(
    "fill",
    function(d) {
      return d.val;
    },
    colorScale
  )
  .renderTo("svg#innerradius");
```

---

## Victory (FormidableLabs)

[Demo/Code](https://codesandbox.io/s/346q5k6nkp)

##### Description:

> An ecosystem of composable React components for building interactive data visualizations

| Licence | Downlods (weekly) | Github stars | Github (Avg time to resolve an issue) | React components | TypeScript support |
| :-----: | ----------------: | -----------: | ------------------------------------: | ---------------- | ------------------ |
|   MIT   |             8,478 |         6034 |                                   6 d | Yes              | No                 |

##### Customizable/Extensible:

* Supports theming
* Exposes APIs to customize the components including: height, width, theme, sortOrder, and it also takes an style prop.
* The style prop should be given as an object with styles defined for data, labels and parent.

```javascript
style={{
  data: {fill: "tomato", opacity: 0.7},
  labels: {fontSize: 12},
  parent: {border: "1px solid #ccc"}
}}
```

##### Dependencies: (7)

* d3-ease
* d3-interpolate
* d3-scale
* d3-shape
* d3-timer
* lodash
* react-fast-compare

##### Browser support:

* N/A

##### Documentation:

* Documentation includes all props, and their types.
* Complex props link into a `Read about it in detail` section that breaks it down even further.
* Includes a FAQ that goes over common questions (example, `How can I change the colors of lines and other elements in Victory?`)

##### Example code block:

```javascript
<VictoryPie
  data={[{ x: "Cats", y: 35 }, { x: "Dogs", y: 40 }, { x: "Birds", y: 55 }]}
/>
```

---

## react-vis (Uber)

[Demo/Code](https://codesandbox.io/s/4z6koov7q9)

##### Description:

> A collection of react components to render common data visualization charts, such as line/area/bar charts, heat maps, scatterplots, contour plots, pie and donut charts, sunbursts, radar charts, parallel coordinates, and tree maps.

| Licence | Downlods (weekly) | Github stars | Github (Avg time to resolve an issue) | React components | TypeScript support |
| :-----: | ----------------: | -----------: | ------------------------------------: | ---------------- | ------------------ |
|   MIT   |              3427 |         3672 |                                  24 d | Yes              | No                 |

##### Customizable/Extensible:

* Supports theming
* **Extremely** customizable, docs explain the four ways to customize:
  * the React-Vis style sheet
  * Class names (selectors)
  * Exposed props (color, width)
  * Style property (you pass an object to the component)

##### Dependencies: (16)

* d3-array
* d3-collection
* d3-color
* d3-contour
* d3-format
* d3-geo
* d3-hierarchy
* d3-interpolate
* d3-sankey
* d3-scale
* d3-shape
* d3-voronoi
* deep-equal
* global
* prop-types
* react-motion

##### Browser support:

* N/A

##### Documentation:

* Not as easy to follow as Victory, requires learning a lot of new technical terms related to D3, and chart/grids
* For an example, searching for `pie charts` chart:
  > ArcSeries for radial arcs such as might be found in pie charts. `Pie Chart == RadialChart`
* Ran into a few broken links
* Each component has an API reference section that goes over all props and their types

##### Example code block:

```javascript
import { EXTENDED_DISCRETE_COLOR_RANGE } from "theme"

<XYPlot
  xDomain={[-3, 3]}
  yDomain={[-3, 3]}
  width={300}
  getAngle={d => d.time}
  getAngle0={d => 0}
  height={300}
>
  <ArcSeries
    animation={{
      damping: 9,
      stiffness: 300
    }}
    radiusDomain={[0, 3]}
    data={[
      { time: seconds / 60 * 2 * PI, radius0: 1, radius: 1.5, color: 0 },
      { time: minutes / 60 * 2 * PI, radius0: 1.6, radius: 2.1, color: 1 },
      { time: hours / 24 * 2 * PI, radius0: 2.2, radius: 2.7, color: 2 }
    ]}
    colorRange={EXTENDED_DISCRETE_COLOR_RANGE}
  />
</XYPlot>
```

---

## Recharts

[Demo/Code](https://codesandbox.io/s/km7ypr0q53)

##### Description:

> Recharts is a Redefined chart library built with React and D3.
>
> The main purpose of this library is to help you to write charts in React applications without any pain. Main principles of Recharts are:
>
> 1.  Simply - deploy with React components
> 2.  Native - SVG support, lightweight depending only on some D3 submodules
> 3.  Declarative - components, components of charts are purely presentational

| Licence | Downlods (weekly) | Github stars | Github (Avg time to resolve an issue) | React components | TypeScript support |
| :-----: | ----------------: | -----------: | ------------------------------------: | ---------------- | ------------------ |
|   MIT   |            25,737 |         9030 |                                   3 d | Yes              | No                 |

##### Customizable/Extensible:

* No support for theming
* Customization is exposed via props
* Does not take class names, or style objects
* Each element has a `fill` prop to pass a colour
* Other areas customization is exposed, changing labels, shape of the bars, and tooltip content.
* Not very customizable, and extensible.

##### Dependencies: (11)

* classnames
* core-js
* d3-interpolate
* d3-scale
* d3-shape
* lodash
* prop-types
* react-resize-detector
* react-smooth
* recharts-scale
* reduce-css-calc

##### Browser support:

* N/A

##### Documentation:

* A lot easier to follow vs `react-vis`, not a lot of technical terms
* List of charts organised and easy to find
* Each chart has a list of available props with their types
* For props that expose `D3` functionality it also includes `D3` doc links

##### Example code block:

```javascript
<PieChart width={730} height={250}>
  <Pie
    data={data01}
    dataKey="value"
    nameKey="name"
    cx="50%"
    cy="50%"
    outerRadius={50}
    fill="#8884d8"
  />
  <Pie
    data={data02}
    dataKey="value"
    nameKey="name"
    cx="50%"
    cy="50%"
    innerRadius={60}
    outerRadius={80}
    fill="#82ca9d"
    label
  />
</PieChart>
```

---

| Libraries                | Pros                                                                                                                                                                           | Cons                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| Plottable (Palantir)     | <ul><li>TypeScript</li><li>Official IE9+ support</li></ul>                                                                                                                     | <ul><li>No React components</li><li>Customization is limited</li><li>Not very popular, and repo isn't actively maintained</li></ul> |
| Victory (FormidableLabs) | <ul><li>React components</li><li>Repo actively maintained</li><li>Theming</li><li>Least num of deps</li><li>Learning curve low</li></ul>                                       | <ul><li>No official TypeScript support</li></ul>                                                                                    |
| react-vis (Uber)         | <ul><li>React components</li><li>Very customizable</li><li>Theming</li><li>Used in Prod by Uber</li></ul>                                                                      | <ul><li>No official TypeScript support</li><li>Docs are a mess</li><li>High learning curve</li><li>Most num of deps</li></ul>       |
| Recharts                 | <ul><li>React components</li><li>Repo actively maintained</li><li>Very popoluar, large community</li><li>Learning curve low</li><li>Docs are easy to read and follow</li></ul> | <ul><li>No official TypeScript support</li><li>No support for theming</li><li>Not very customizable, and extensible.</li></ul>      |
