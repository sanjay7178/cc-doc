---
title: Job Statistics Schema
description: ClusterCockpit Job Statistics Schema Reference
categories: [cc-backend]
tags: [Backend]
weight: 4
---

# Job statistics

- [1. [Required] Property Job statistics > unit](#unit)
  - [1.1. [Required] Property Job statistics > unit > base](#unit_base)
  - [1.2. [Optional] Property Job statistics > unit > prefix](#unit_prefix)
- [2. [Required] Property Job statistics > avg](#avg)
- [3. [Required] Property Job statistics > min](#min)
- [4. [Required] Property Job statistics > max](#max)

**Title:** Job statistics

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Format specification for job metric statistics

<details>
<summary>
<strong> <a name="unit"></a>1. [Required] Property Job statistics > unit</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |
| **Defined in**            | unit.schema.json                                                          |

**Description:** Metric unit

<details>
<summary>
<strong> <a name="unit_base"></a>1.1. [Required] Property Job statistics > unit > base</strong>  

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
<strong> <a name="unit_prefix"></a>1.2. [Optional] Property Job statistics > unit > prefix</strong>  

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

</blockquote>
</details>

<details>
<summary>
<strong> <a name="avg"></a>2. [Required] Property Job statistics > avg</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `number` |
| **Required** | Yes      |

**Description:** Job metric average

| Restrictions |        |
| ------------ | ------ |
| **Minimum**  | &ge; 0 |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="min"></a>3. [Required] Property Job statistics > min</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `number` |
| **Required** | Yes      |

**Description:** Job metric minimum

| Restrictions |        |
| ------------ | ------ |
| **Minimum**  | &ge; 0 |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="max"></a>4. [Required] Property Job statistics > max</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `number` |
| **Required** | Yes      |

**Description:** Job metric maximum

| Restrictions |        |
| ------------ | ------ |
| **Minimum**  | &ge; 0 |

</blockquote>
</details>

----------------------------------------------------------------------------------------------------------------------------
Generated using [json-schema-for-humans](https://github.com/coveooss/json-schema-for-humans) on 2024-02-02 at 14:36:54 +0100