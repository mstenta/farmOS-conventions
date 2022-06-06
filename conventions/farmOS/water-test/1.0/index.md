# Water test

**Version 1.0**

```yml
convention_id: "farmOS:water-test:1.0"
dependencies:
  - farm:farm_lab_test
```

## Purpose

Water tests are used to represent the act of collecting a water sample, sending
it to a water testing lab, receiving test results back, and storing data for
future reference.

## Specification

Water tests MUST be recorded as a "Lab test" (`lab_test`) log. The "Test type"
(`lab_test_type`) field MUST be set to "Water test" (`water`).

The "Timestamp" (`timestamp`) field of the log MUST be the date when the
sample(s) were collected. The "Received date" (`lab_received_date`) field MAY
contain the date when the lab received the sample, and the "Processed date"
(`lab_processed_date`) MAY contain the date when the lab processed the sample.

Test results MUST be recorded as quantities referenced by the log's "Quantities"
(`quantity`) field, and the quantity type MUST be "Test" (`test`). The quantity
"Value" (`value`) and "Units" (`units`) MUST match the values/units returned by
the lab. Each quantity SHOULD include the laboratory testing method that was
used to obtain the value in the "Test method" (`test_method`) field. Quantities
MUST include a "Label" (`label`) to represent the water indicator that is being
measured. This label SHOULD match the machine name or CSV column header from the
lab, or if that is not available then the human-readable label included in the
lab results report. Quantities MAY include a "Measure" (`measure`), but no
guidance is provided for recommended measures at this time.

Lab test logs SHOULD reference the lab that performed the tests in the
"Laboratory" (`lab`) field. The referenced lab will be a taxonomy term that MAY
include additional information about the lab.

Lab test logs MAY include the location(s) that sample(s) were collected from in
the "Geometry" (`geometry`) field. If a single GPS point is used, then it is
assumed that the sample was collected from that point. If multiple GPS points
are used, then it is assumed that multiple sample(s) were collected and mixed
together into a single sample before being sent to the lab. If a polygon is
used, then it is assumed that granular point locations are not available, and
the results should be broadly interpretted for the whole area. Other geometry
types SHOULD NOT be used.

In addition to specific geometries, Lab test logs MAY also reference specific
Land (or other) assets in the "Location" (`location`) field to indicate where
the sample(s) were collected from for easier searching/filtering purposes.
