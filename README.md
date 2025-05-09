````markdown

# Choropleth Map Visualization

This README outlines how to build a choropleth map that visualizes education data across the United States using D3.js, HTML, CSS, and JavaScript. The application meets the requirements outlined by FreeCodeCamp, ensuring a functional and engaging user experience.

## Objective

The goal is to create a web application like [this example](https://choropleth-map.freecodecamp.rocks), fulfilling several user stories, and enabling users to visualize education data through a colorful map.

## User Stories

Your app should satisfy the following user stories:

1. **Title:** Your choropleth should have a title with `id="title"`.
2. **Description:** Your choropleth should have a description element with `id="description"`.
3. **Counties:** Your choropleth should have counties with the class `county` that represent the data.
4. **Fill Colors:** There should be at least 4 different fill colors used for the counties.
5. **Data Properties:** Each county should have `data-fips` and `data-education` properties for its corresponding values.
6. **Complete Data Representation:** Your choropleth should have a county for each provided data point.
7. **Matching Values:** The counties should have matching `data-fips` and `data-education` values as per sample data.
8. **Legend:** Your choropleth should have a legend with `id="legend"`.
9. **Colored Legend:** There should be at least 4 different fill colors used for the legend.
10. **Tooltip:** You should be able to mouse over an area and see a tooltip with `id="tooltip"` that displays more information.
11. **Tooltip Data Property:** The tooltip should have a `data-education` property that corresponds to the `data-education` of the active area.

## Datasets

You will need the following datasets to complete the project:

- US Education Data: [Education Data JSON](https://cdn.freecodecamp.org/testable-projects-fcc/data/choropleth_map/for_user_education.json)
- US County Data: [County Data JSON](https://cdn.freecodecamp.org/testable-projects-fcc/data/choropleth_map/counties.json)

## File Structure

Here's a simple folder structure for your project:

```
/choropleth-map
|-- index.html
|-- styles.css
|-- script.js
```

## Getting Started

### 1. `index.html`

Create an HTML file to structure your app:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Choropleth Map</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1 id="title">US Education Levels by County</h1>
    <p id="description">This choropleth map visualizes the education levels across counties in the United States based on data.</p>
    <svg id="choropleth" width="960" height="600"></svg>
    <div id="legend"></div>
    <div id="tooltip" class="tooltip" style="opacity: 0;"></div>
    
    <script src="https://d3js.org/d3.v6.min.js"></script>
    <script src="script.js"></script>
</body>
</html>
```

### 2. `styles.css`

Write your CSS for styling:

```css
body {
    font-family: Arial, sans-serif;
}

#tooltip {
    position: absolute;
    text-align: center;
    padding: 5px;
    background: lightsteelblue;
    border: 1px solid gray;
    border-radius: 3px;
    pointer-events: none; /* Prevent tooltip from interfering with mouse events */
}

.county {
    stroke: #fff;
    stroke-width: 1;
}

#legend {
    display: flex;
    justify-content: space-between;
    width: 300px;
    margin: 20px auto;
}

.legend-item {
    height: 20px;
    width: 20px;
    border: 1px solid #000;
    display: inline-block;
}
```

### 3. `script.js`

Implement D3.js to create the choropleth map:

```javascript
const width = 960;
const height = 600;

// Load Data
Promise.all([
    d3.json("https://cdn.freecodecamp.org/testable-projects-fcc/data/choropleth_map/for_user_education.json"),
    d3.json("https://cdn.freecodecamp.org/testable-projects-fcc/data/choropleth_map/counties.json"),
]).then(data => {
    const educationData = data[0];
    const counties = data[1
