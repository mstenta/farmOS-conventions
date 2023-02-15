# {{ Name }}

**Version {{ Version number }}**

```yml
convention_id: "{{ namespace + slug + version, colon separated (eg: farm:my-convention:1.0) }}"
inherits_from:
  - {{ (Optional list of convention IDs that this convention inherits from/extends }}
related_conventions:
  - {{ (Optional list of convention IDs that this convention is related to }}
dependencies:
  - {{ List of farmOS module dependencies }}
```

## Purpose

{{ Required. Describe the purpose of this convention. }}

## Specification

{{ Required. Describe the data structure, using RFC 2119 key words to indicate requirements. }}

## Notable implementations

{{ Optional. Places where this convention is used in farmOS core/contrib. }}
