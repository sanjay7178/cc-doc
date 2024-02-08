---
title: Unit Schema
description: ClusterCockpit Unit Schema Reference
categories: [cc-backend]
tags: [Backend]
weight: 5
---

The following schema in its raw form can be found in the [ClusterCockpit GitHub](https://github.com/ClusterCockpit/cc-backend/tree/master/pkg/schema/schemas) repository.

{{< alert title="Manual Updates">}}
  Changes to the original JSON schema found in the repository are not automatically rendered in this reference documentation.</br></br>
  **Last Update:** 02.02.2024
{{< /alert >}}

## Metric unit

- [1. [Required] Property Metric unit > base](#base)
- [2. [Optional] Property Metric unit > prefix](#prefix)

**Title:** Metric unit

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Format specification for job metric units

<details>
<summary>
<strong> <a name="base"></a>1. [Required] Property Metric unit > base</strong>  

</summary>
<blockquote>

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | Yes                |

**Description:** Metric base unit

Must be one of:
* "B"
* "F"
* "B/s"
* "F/s"
* "CPI"
* "IPC"
* "Hz"
* "W"
* "°C"
* ""

</blockquote>
</details>

<details>
<summary>
<strong> <a name="prefix"></a>2. [Optional] Property Metric unit > prefix</strong>  

</summary>
<blockquote>

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | No                 |

**Description:** Unit prefix

Must be one of:
* "K"
* "M"
* "G"
* "T"
* "P"
* "E"

</blockquote>
</details>

----------------------------------------------------------------------------------------------------------------------------
Generated using [json-schema-for-humans](https://github.com/coveooss/json-schema-for-humans) on 2024-02-02 at 14:36:54 +0100