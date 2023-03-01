# Land Asset

**Version 1.0**

```yml
convention_id: "farmOS:land:1.0"
dependencies:
  - farm:farm_land
```

## Purpose

A land asset is a unique geographic area, defined by a polygon. Land assets
are used both to provide a visual representation of specific areas of land on a
map, as well as a reference point to organize other records associated with the
geographic area.

## Specification

A specific area of land MUST be recorded as a "Land" (`land`) asset.

Land assets MUST have a name (`name`).

The "Land type" (`land_type`) field MUST be set to indicate the primary use of
the area. Land types are provided by modules, and MAY include options like
"Field" (`field`), "Paddock" (`paddock`), or "Property" (`property`). If an
appropriate land type is not available, "Other" (`other`) MAY be selected.

Land assets SHOULD include a polygon that represents their geographic boundaries
in the "Intrinsic geometry" (`intrinsic geometry`) field. The "Is fixed"
(`is_fixed`) boolean field MUST be set to true to indicate that it has a fixed
geometry.

Generally speaking, the geometry of a land asset should not change over time. If
significant changes are made to the geographic area which necessitate changing
the polygon geometry, then best practice is to create a new land asset and
archive the old one. The exception to this is minor adjustments or corrections,
which do not indicate actual changes to the geographic area in the real world.

The "Is location" (`is_location`) boolean field SHOULD be set to true to
indicate that other assets can be moved to the land asset.

When a land asset is actively being managed, the Status (`status`) field SHOULD
be set to "Active" (`active`). When it is no longer being managed, it SHOULD be
set to "Archived" (`archived`). Land assets MAY move back and forth between
"Active" and "Archived" status depending on their management activities.
