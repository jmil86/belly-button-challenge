# belly-button-challenge


This README provides a summary of the crucial JavaScript code used.

## `buildMetadata(sample)` Function:

* `d3.json(...).then((data) => {`: Fetches JSON data.
* `let metadata = data.metadata;`: Extracts metadata array.
* `let resultArray = metadata.filter(...);`: Filters metadata for the selected sample.
* `let result = resultArray[0];`: Gets the matching metadata object.
* `let PANEL = d3.select("#sample-metadata");`: Selects the metadata display panel.
* `PANEL.html("");`: Clears existing panel content.
* `Object.entries(result).forEach(([key, value]) => {`: Iterates through metadata key-value pairs.
* `PANEL.append("h6").text(...);`: Appends metadata to the panel.

## `buildCharts(sample)` Function:

* `d3.json(...).then((data) => {`: Fetches JSON data for charts.
* `let samples = data.samples;`: Extracts sample data.
* `let resultArray = samples.filter(...);`: Filters samples for the selected sample.
* `let result = resultArray[0];`: Gets the matching sample object.
* `let otu_ids = result.otu_ids;`: Extracts OTU IDs.
* `let otu_labels = result.otu_labels;`: Extracts OTU labels.
* `let sample_values = result.sample_values;`: Extracts sample values.
* `let bubbleLayout = { ... };`: Defines bubble chart layout.
* `let bubbleData = [ { ... } ];`: Defines bubble chart data.
* `Plotly.newPlot("bubble", bubbleData, bubbleLayout);`: Renders bubble chart.
* `let yticks = otu_ids.slice(0, 10).map(...).reverse();`: Prepares bar chart y-axis labels.
* `let barData = [ { ... } ];`: Defines bar chart data.
* `let barLayout = { ... };`: Defines bar chart layout.
* `Plotly.newPlot("bar", barData, barLayout);`: Renders bar chart.

## `init()` Function:

* `d3.json(...).then((data) => {`: Fetches JSON data for initialization.
* `let sampleNames = data.names;`: Extracts sample names.
* `let selector = d3.select("#selDataset");`: Selects dropdown element.
* `sampleNames.forEach((sample) => {`: Iterates through sample names.
* `d3.select("#selDataset").append("option").text(...).property("value", sample);`: Appends dropdown options.
* `let firstSample = sampleNames[0];`: Gets the first sample.
* `buildCharts(firstSample);`: Builds initial charts.
* `buildMetadata(firstSample);`: Builds initial metadata.

## `optionChanged(newSample)` Function:

* `function optionChanged(newSample) {`: Defines function for dropdown change.
* `buildCharts(newSample);`: Updates charts on sample change.
* `buildMetadata(newSample);`: Updates metadata on sample change.

## Initialization:

* `init();`: Initializes the dashboard.