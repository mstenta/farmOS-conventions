# Animal weight

**Version 1.0**

```yml
convention_id: "farmOS:animal-weight:1.0"
dependencies:
  - farm:farm_animal
  - farm:farm_observation
```

## Purpose

Animal weight measurements are used to track animal growth over time.

## Specification

Animal weight measurements MUST be recorded as Observation (`observation`) logs.

The "Timestamp" (`timestamp`) field of the log MUST be the date when the
animal's weight was measured.

The "Assets" (`asset`) field of the log MUST reference one or more Animal
(`animal`) assets, which represent the animal(s) being weighed. If multiple
animal assets are referenced, the weight value MUST be the average weight of all
animals (not the sum total weight of all animals). Weights MAY be estimated.

Weight MUST be recorded as a single quantity referenced by the log's
"Quantities" (`quantity`) field, and the quantity type MUST be "Standard"
(`standard`). The quantity "Measure" (`measure`) must be "Weight" (`weight`),
and the quantity "Value" (`value`) must be the numeric weight value. The
quantity "Units" (`units`) MAY be any unit of weight measurement, but the
following recommended units SHOULD be used when possible for consistency:

If the system of measurement is "US" (`us`), units SHOULD be "lbs".
If the system of measurement is "Metric" (`metric`), units SHOULD be "kg".

An animal's current weight MUST be calculated by looking at the quantity value
and units of the most recent completed (`status` is `done`) weight observation
log that references the animal. Projected weight gain MAY be simulated by
creating weight observation logs with a future date that are not completed
(`status` is `pending`).

## Notable implementations

- Birth quick form
- [Animal weight module](https://www.drupal.org/project/farm_animal_weight)
