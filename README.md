**Proof of concept only**

# Leaflet.SLDStyler

Apply styling from 1.1.0 or 1.0 SLD-File to a GeoJSON layer.

Rules can be ORed or ANDed. The following comparisions are possible:

 * ogc:PropertyIsEqualTo
 * ogc:PropertyIsNotEqualTo
 * ogc:PropertyIsLessThan
 * ogc:PropertyIsGreaterThan
 * ogc:PropertyIsLessThanOrEqualTo
 * ogc:PropertyIsGreaterThanOrEqualTo

The following PolygonSymbolizer properties are applied:

 * stroke
 * stroke-width
 * stroke-opacity
 * fill-opacity
 * fill
 * stroke-opacity
 * stroke-dasharray
 * stroke-linejoin
 * stroke-linecap

Also see the unit tests for what is possible.

Example:

    var SLDStyler = new L.SLDStyler(SLDXmlOrText);

    var geojsonLayer = L.geoJson(jsonObject, {
       style: SLDStyler.getStyleFunction()
    }).addTo(map);

Of course, here's an example of how the chapter for the `readme.md` explaining how to use the `LeafletSldLegend` class could be in English:

# Using the Legend generator

The `LeafletSldLegend` class is used to generate graphical legends from an SLD (Styled Layer Descriptor) XML document that describes the styles of a layer on a map. These legends are useful for visually representing the style rules defined in the SLD.

## Installation

To use the `LeafletSldLegend` class, first ensure you have a compatible JavaScript environment. Then, you can import the class into your project:

```javascript
import LeafletSldLegend from './LeafletSldLegend'; // Make sure the path is correct
```

## Creating an Instance

To create an instance of `LeafletSldLegend`, provide an SLD XML document as an argument to the constructor. Make sure the SLD document is in string form. Here's an example of how to do it:

```javascript
const sldXml = `
    <StyledLayerDescriptor version="1.1.0" xmlns="http://www.opengis.net/sld">
        <!-- Define your styles here -->
    </StyledLayerDescriptor>
`;

const legend = new LeafletSldLegend(sldXml);
```

## Generating Legends

Once you've created an instance of `LeafletSldLegend`, you can generate graphical legends for your styles defined in the SLD. The legend information is stored in the `legend` object created earlier. You can access legends for each layer and style rule as follows:

```javascript
// Get the layers in the SLD
const layers = Object.keys(legend.legend);

// Iterate through layers and their style rules
layers.forEach(layerName => {
    const layer = legend.legend[layerName];
    console.log(`Layer: ${layerName}`);

    // Iterate through style rules of the layer
    layer.rules.forEach(rule => {
        console.log(`Rule: ${rule.name}`);
        console.log(`Title: ${rule.title}`);
        console.log(`SVG for the rule:`);
        console.log(rule.svg);
    });
});
```

The above code will print information about layers and style rules to the console, along with the associated SVG for each rule.


To be done:
 * more styling properties and comparisions
