# Anonymized Location Extension Specification

- **Title:** Anonymized Location
- **Identifier:** <https://stac-extensions.github.io/anonymized-location/v1.0.0/schema.json>
- **Field Name Prefix:** anon
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @kbgg @duckontheweb

This document explains the Anonymized Location Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.
Some imagery can not be shared with precise location information either due to provider requirements or for privacy concerns.
In these cases, the imagery can be assigned to a bounding box contained in a grid of arbritrary size.
Larger bounding boxes are more anonymized but the usefulness of the data diminishes as the bounding box grows.
To allow for the size of this bounding box to match the privacy and usefulness requirements of the data, a precision property can be defined.

- Examples:
  - [Item example](examples/su_african_crops/su_african_crops_labels/su_african_crops_labels_ghana_000000.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/su_african_crops/su_african_crops_source/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Item Properties and Collection Fields

| Field Name           | Type                      | Description |
| -------------------- | ------------------------- | ----------- |
| anon:size            | number                    | **REQUIRED**. The size of one side of the anonymized bounding box in degrees. For example, if this value is set to 2 then the bounding box for the items should be 2 degrees latitude by 2 degrees longitude. |
| anon:warning         | string                    | **REQUIRED**. A brief warning that the geometry of the item is not accurate and a description of how it has been anonymized. |

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
