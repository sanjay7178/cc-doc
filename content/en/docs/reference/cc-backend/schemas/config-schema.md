---
title: Application Config Schema
description: ClusterCockpit Application Config Schema Reference
categories: [cc-backend]
tags: [Backend]
weight: 1
---

A detailed description of each of the application configuration options can be found in the [config documentation]({{< ref "configuration" >}} "CC-Backend Configuration").

The following schema in its raw form can be found in the [ClusterCockpit GitHub](https://github.com/ClusterCockpit/cc-backend/tree/master/pkg/schema/schemas) repository.

{{< alert title="Manual Updates">}}
  Changes to the original JSON schema found in the repository are not automatically rendered in this reference documentation.</br></br>
  **Last Update:** 02.02.2024
{{< /alert >}}

## cc-backend configuration file schema

- [1. [Optional] Property cc-backend configuration file schema > addr](#addr)
- [2. [Optional] Property cc-backend configuration file schema > user](#user)
- [3. [Optional] Property cc-backend configuration file schema > group](#group)
- [4. [Optional] Property cc-backend configuration file schema > disable-authentication](#disable-authentication)
- [5. [Optional] Property cc-backend configuration file schema > embed-static-files](#embed-static-files)
- [6. [Optional] Property cc-backend configuration file schema > static-files](#static-files)
- [7. [Optional] Property cc-backend configuration file schema > db-driver](#db-driver)
- [8. [Optional] Property cc-backend configuration file schema > db](#db)
- [9. [Optional] Property cc-backend configuration file schema > job-archive](#job-archive)
  - [9.1. [Required] Property cc-backend configuration file schema > job-archive > kind](#job-archive_kind)
  - [9.2. [Optional] Property cc-backend configuration file schema > job-archive > path](#job-archive_path)
  - [9.3. [Optional] Property cc-backend configuration file schema > job-archive > compression](#job-archive_compression)
  - [9.4. [Optional] Property cc-backend configuration file schema > job-archive > retention](#job-archive_retention)
    - [9.4.1. [Required] Property cc-backend configuration file schema > job-archive > retention > policy](#job-archive_retention_policy)
    - [9.4.2. [Optional] Property cc-backend configuration file schema > job-archive > retention > includeDB](#job-archive_retention_includeDB)
    - [9.4.3. [Optional] Property cc-backend configuration file schema > job-archive > retention > age](#job-archive_retention_age)
    - [9.4.4. [Optional] Property cc-backend configuration file schema > job-archive > retention > location](#job-archive_retention_location)
- [10. [Optional] Property cc-backend configuration file schema > disable-archive](#disable-archive)
- [11. [Optional] Property cc-backend configuration file schema > validate](#validate)
- [12. [Optional] Property cc-backend configuration file schema > session-max-age](#session-max-age)
- [13. [Optional] Property cc-backend configuration file schema > https-cert-file](#https-cert-file)
- [14. [Optional] Property cc-backend configuration file schema > https-key-file](#https-key-file)
- [15. [Optional] Property cc-backend configuration file schema > redirect-http-to](#redirect-http-to)
- [16. [Optional] Property cc-backend configuration file schema > stop-jobs-exceeding-walltime](#stop-jobs-exceeding-walltime)
- [17. [Optional] Property cc-backend configuration file schema > short-running-jobs-duration](#short-running-jobs-duration)
- [18. [Required] Property cc-backend configuration file schema > jwts](#jwts)
  - [18.1. [Required] Property cc-backend configuration file schema > jwts > max-age](#jwts_max-age)
  - [18.2. [Optional] Property cc-backend configuration file schema > jwts > cookieName](#jwts_cookieName)
  - [18.3. [Optional] Property cc-backend configuration file schema > jwts > validateUser](#jwts_validateUser)
  - [18.4. [Optional] Property cc-backend configuration file schema > jwts > trustedIssuer](#jwts_trustedIssuer)
  - [18.5. [Optional] Property cc-backend configuration file schema > jwts > syncUserOnLogin](#jwts_syncUserOnLogin)
- [19. [Optional] Property cc-backend configuration file schema > ldap](#ldap)
  - [19.1. [Required] Property cc-backend configuration file schema > ldap > url](#ldap_url)
  - [19.2. [Required] Property cc-backend configuration file schema > ldap > user_base](#ldap_user_base)
  - [19.3. [Required] Property cc-backend configuration file schema > ldap > search_dn](#ldap_search_dn)
  - [19.4. [Required] Property cc-backend configuration file schema > ldap > user_bind](#ldap_user_bind)
  - [19.5. [Required] Property cc-backend configuration file schema > ldap > user_filter](#ldap_user_filter)
  - [19.6. [Optional] Property cc-backend configuration file schema > ldap > username_attr](#ldap_username_attr)
  - [19.7. [Optional] Property cc-backend configuration file schema > ldap > sync_interval](#ldap_sync_interval)
  - [19.8. [Optional] Property cc-backend configuration file schema > ldap > sync_del_old_users](#ldap_sync_del_old_users)
  - [19.9. [Optional] Property cc-backend configuration file schema > ldap > syncUserOnLogin](#ldap_syncUserOnLogin)
- [20. [Required] Property cc-backend configuration file schema > clusters](#clusters)
  - [20.1. cc-backend configuration file schema > clusters > clusters items](#autogenerated_heading_2)
    - [20.1.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > name](#clusters_items_name)
    - [20.1.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository](#clusters_items_metricDataRepository)
      - [20.1.2.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository > kind](#clusters_items_metricDataRepository_kind)
      - [20.1.2.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository > url](#clusters_items_metricDataRepository_url)
      - [20.1.2.3. [Optional] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository > token](#clusters_items_metricDataRepository_token)
    - [20.1.3. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges](#clusters_items_filterRanges)
      - [20.1.3.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > numNodes](#clusters_items_filterRanges_numNodes)
        - [20.1.3.1.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > numNodes > from](#clusters_items_filterRanges_numNodes_from)
        - [20.1.3.1.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > numNodes > to](#clusters_items_filterRanges_numNodes_to)
      - [20.1.3.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > duration](#clusters_items_filterRanges_duration)
        - [20.1.3.2.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > duration > from](#clusters_items_filterRanges_duration_from)
        - [20.1.3.2.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > duration > to](#clusters_items_filterRanges_duration_to)
      - [20.1.3.3. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > startTime](#clusters_items_filterRanges_startTime)
        - [20.1.3.3.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > startTime > from](#clusters_items_filterRanges_startTime_from)
        - [20.1.3.3.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > startTime > to](#clusters_items_filterRanges_startTime_to)
- [21. [Optional] Property cc-backend configuration file schema > ui-defaults](#ui-defaults)
  - [21.1. [Required] Property cc-backend configuration file schema > ui-defaults > plot_general_colorBackground](#ui-defaults_plot_general_colorBackground)
  - [21.2. [Required] Property cc-backend configuration file schema > ui-defaults > plot_general_lineWidth](#ui-defaults_plot_general_lineWidth)
  - [21.3. [Required] Property cc-backend configuration file schema > ui-defaults > plot_list_jobsPerPage](#ui-defaults_plot_list_jobsPerPage)
  - [21.4. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_plotsPerRow](#ui-defaults_plot_view_plotsPerRow)
  - [21.5. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_showPolarplot](#ui-defaults_plot_view_showPolarplot)
  - [21.6. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_showRoofline](#ui-defaults_plot_view_showRoofline)
  - [21.7. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_showStatTable](#ui-defaults_plot_view_showStatTable)
  - [21.8. [Required] Property cc-backend configuration file schema > ui-defaults > system_view_selectedMetric](#ui-defaults_system_view_selectedMetric)
  - [21.9. [Required] Property cc-backend configuration file schema > ui-defaults > analysis_view_histogramMetrics](#ui-defaults_analysis_view_histogramMetrics)
    - [21.9.1. cc-backend configuration file schema > ui-defaults > analysis_view_histogramMetrics > analysis_view_histogramMetrics items](#autogenerated_heading_3)
  - [21.10. [Required] Property cc-backend configuration file schema > ui-defaults > analysis_view_scatterPlotMetrics](#ui-defaults_analysis_view_scatterPlotMetrics)
    - [21.10.1. cc-backend configuration file schema > ui-defaults > analysis_view_scatterPlotMetrics > analysis_view_scatterPlotMetrics items](#autogenerated_heading_4)
      - [21.10.1.1. cc-backend configuration file schema > ui-defaults > analysis_view_scatterPlotMetrics > analysis_view_scatterPlotMetrics items > analysis_view_scatterPlotMetrics items items](#autogenerated_heading_5)
  - [21.11. [Required] Property cc-backend configuration file schema > ui-defaults > job_view_nodestats_selectedMetrics](#ui-defaults_job_view_nodestats_selectedMetrics)
    - [21.11.1. cc-backend configuration file schema > ui-defaults > job_view_nodestats_selectedMetrics > job_view_nodestats_selectedMetrics items](#autogenerated_heading_6)
  - [21.12. [Required] Property cc-backend configuration file schema > ui-defaults > job_view_polarPlotMetrics](#ui-defaults_job_view_polarPlotMetrics)
    - [21.12.1. cc-backend configuration file schema > ui-defaults > job_view_polarPlotMetrics > job_view_polarPlotMetrics items](#autogenerated_heading_7)
  - [21.13. [Required] Property cc-backend configuration file schema > ui-defaults > job_view_selectedMetrics](#ui-defaults_job_view_selectedMetrics)
    - [21.13.1. cc-backend configuration file schema > ui-defaults > job_view_selectedMetrics > job_view_selectedMetrics items](#autogenerated_heading_8)
  - [21.14. [Required] Property cc-backend configuration file schema > ui-defaults > plot_general_colorscheme](#ui-defaults_plot_general_colorscheme)
    - [21.14.1. cc-backend configuration file schema > ui-defaults > plot_general_colorscheme > plot_general_colorscheme items](#autogenerated_heading_9)
  - [21.15. [Required] Property cc-backend configuration file schema > ui-defaults > plot_list_selectedMetrics](#ui-defaults_plot_list_selectedMetrics)
    - [21.15.1. cc-backend configuration file schema > ui-defaults > plot_list_selectedMetrics > plot_list_selectedMetrics items](#autogenerated_heading_10)

**Title:** cc-backend configuration file schema

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

<details>
<summary>
<strong> <a name="addr"></a>1. [Optional] Property cc-backend configuration file schema > addr</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Address where the http (or https) server will listen on (for example: 'localhost:80').

</blockquote>
</details>

<details>
<summary>
<strong> <a name="user"></a>2. [Optional] Property cc-backend configuration file schema > user</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Drop root permissions once .env was read and the port was taken. Only applicable if using privileged port.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="group"></a>3. [Optional] Property cc-backend configuration file schema > group</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Drop root permissions once .env was read and the port was taken. Only applicable if using privileged port.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="disable-authentication"></a>4. [Optional] Property cc-backend configuration file schema > disable-authentication</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Disable authentication (for everything: API, Web-UI, ...).

</blockquote>
</details>

<details>
<summary>
<strong> <a name="embed-static-files"></a>5. [Optional] Property cc-backend configuration file schema > embed-static-files</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** If all files in `web/frontend/public` should be served from within the binary itself (they are embedded) or not.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="static-files"></a>6. [Optional] Property cc-backend configuration file schema > static-files</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Folder where static assets can be found, if embed-static-files is false.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="db-driver"></a>7. [Optional] Property cc-backend configuration file schema > db-driver</strong>  

</summary>
<blockquote>

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | No                 |

**Description:** sqlite3 or mysql (mysql will work for mariadb as well).

Must be one of:
* "sqlite3"
* "mysql"

</blockquote>
</details>

<details>
<summary>
<strong> <a name="db"></a>8. [Optional] Property cc-backend configuration file schema > db</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** For sqlite3 a filename, for mysql a DSN in this format: https://github.com/go-sql-driver/mysql#dsn-data-source-name (Without query parameters!).

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive"></a>9. [Optional] Property cc-backend configuration file schema > job-archive</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Configuration keys for job-archive

<details>
<summary>
<strong> <a name="job-archive_kind"></a>9.1. [Required] Property cc-backend configuration file schema > job-archive > kind</strong>  

</summary>
<blockquote>

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | Yes                |

**Description:** Backend type for job-archive

Must be one of:
* "file"
* "s3"

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive_path"></a>9.2. [Optional] Property cc-backend configuration file schema > job-archive > path</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Path to job archive for file backend

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive_compression"></a>9.3. [Optional] Property cc-backend configuration file schema > job-archive > compression</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | No        |

**Description:** Setup automatic compression for jobs older than number of days

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive_retention"></a>9.4. [Optional] Property cc-backend configuration file schema > job-archive > retention</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Configuration keys for retention

<details>
<summary>
<strong> <a name="job-archive_retention_policy"></a>9.4.1. [Required] Property cc-backend configuration file schema > job-archive > retention > policy</strong>  

</summary>
<blockquote>

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | Yes                |

**Description:** Retention policy

Must be one of:
* "none"
* "delete"
* "move"

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive_retention_includeDB"></a>9.4.2. [Optional] Property cc-backend configuration file schema > job-archive > retention > includeDB</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Also remove jobs from database

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive_retention_age"></a>9.4.3. [Optional] Property cc-backend configuration file schema > job-archive > retention > age</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | No        |

**Description:** Act on jobs with startTime older than age (in days)

</blockquote>
</details>

<details>
<summary>
<strong> <a name="job-archive_retention_location"></a>9.4.4. [Optional] Property cc-backend configuration file schema > job-archive > retention > location</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** The target directory for retention. Only applicable for retention move.

</blockquote>
</details>

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="disable-archive"></a>10. [Optional] Property cc-backend configuration file schema > disable-archive</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Keep all metric data in the metric data repositories, do not write to the job-archive.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="validate"></a>11. [Optional] Property cc-backend configuration file schema > validate</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Validate all input json documents against json schema.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="session-max-age"></a>12. [Optional] Property cc-backend configuration file schema > session-max-age</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Specifies for how long a session shall be valid  as a string parsable by time.ParseDuration(). If 0 or empty, the session/token does not expire!

</blockquote>
</details>

<details>
<summary>
<strong> <a name="https-cert-file"></a>13. [Optional] Property cc-backend configuration file schema > https-cert-file</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Filepath to SSL certificate. If also https-key-file is set use HTTPS using those certificates.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="https-key-file"></a>14. [Optional] Property cc-backend configuration file schema > https-key-file</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Filepath to SSL key file. If also https-cert-file is set use HTTPS using those certificates.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="redirect-http-to"></a>15. [Optional] Property cc-backend configuration file schema > redirect-http-to</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** If not the empty string and addr does not end in :80, redirect every request incoming at port 80 to that url.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="stop-jobs-exceeding-walltime"></a>16. [Optional] Property cc-backend configuration file schema > stop-jobs-exceeding-walltime</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | No        |

**Description:** If not zero, automatically mark jobs as stopped running X seconds longer than their walltime. Only applies if walltime is set for job.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="short-running-jobs-duration"></a>17. [Optional] Property cc-backend configuration file schema > short-running-jobs-duration</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | No        |

**Description:** Do not show running jobs shorter than X seconds.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="jwts"></a>18. [Required] Property cc-backend configuration file schema > jwts</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** For JWT token authentication.

<details>
<summary>
<strong> <a name="jwts_max-age"></a>18.1. [Required] Property cc-backend configuration file schema > jwts > max-age</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Configure how long a token is valid. As string parsable by time.ParseDuration()

</blockquote>
</details>

<details>
<summary>
<strong> <a name="jwts_cookieName"></a>18.2. [Optional] Property cc-backend configuration file schema > jwts > cookieName</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Cookie that should be checked for a JWT token.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="jwts_validateUser"></a>18.3. [Optional] Property cc-backend configuration file schema > jwts > validateUser</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Deny login for users not in database (but defined in JWT). Overwrite roles in JWT with database roles.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="jwts_trustedIssuer"></a>18.4. [Optional] Property cc-backend configuration file schema > jwts > trustedIssuer</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Issuer that should be accepted when validating external JWTs 

</blockquote>
</details>

<details>
<summary>
<strong> <a name="jwts_syncUserOnLogin"></a>18.5. [Optional] Property cc-backend configuration file schema > jwts > syncUserOnLogin</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Add non-existent user to DB at login attempt with values provided in JWT.

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap"></a>19. [Optional] Property cc-backend configuration file schema > ldap</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** For LDAP Authentication and user synchronisation.

<details>
<summary>
<strong> <a name="ldap_url"></a>19.1. [Required] Property cc-backend configuration file schema > ldap > url</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** URL of LDAP directory server.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_user_base"></a>19.2. [Required] Property cc-backend configuration file schema > ldap > user_base</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Base DN of user tree root.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_search_dn"></a>19.3. [Required] Property cc-backend configuration file schema > ldap > search_dn</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** DN for authenticating LDAP admin account with general read rights.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_user_bind"></a>19.4. [Required] Property cc-backend configuration file schema > ldap > user_bind</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Expression used to authenticate users via LDAP bind. Must contain uid={username}.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_user_filter"></a>19.5. [Required] Property cc-backend configuration file schema > ldap > user_filter</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Filter to extract users for syncing.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_username_attr"></a>19.6. [Optional] Property cc-backend configuration file schema > ldap > username_attr</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Attribute with full username. Default: gecos

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_sync_interval"></a>19.7. [Optional] Property cc-backend configuration file schema > ldap > sync_interval</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

**Description:** Interval used for syncing local user table with LDAP directory. Parsed using time.ParseDuration.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_sync_del_old_users"></a>19.8. [Optional] Property cc-backend configuration file schema > ldap > sync_del_old_users</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Delete obsolete users in database.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ldap_syncUserOnLogin"></a>19.9. [Optional] Property cc-backend configuration file schema > ldap > syncUserOnLogin</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | No        |

**Description:** Add non-existent user to DB at login attempt if user exists in Ldap directory

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters"></a>20. [Required] Property cc-backend configuration file schema > clusters</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of object` |
| **Required** | Yes               |

**Description:** Configuration for the clusters to be displayed.

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be   | Description |
| --------------------------------- | ----------- |
| [clusters items](#clusters_items) | -           |

### <a name="autogenerated_heading_2"></a>20.1. cc-backend configuration file schema > clusters > clusters items

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

<details>
<summary>
<strong> <a name="clusters_items_name"></a>20.1.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > name</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** The name of the cluster.

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_metricDataRepository"></a>20.1.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Type of the metric data repository for this cluster

<details>
<summary>
<strong> <a name="clusters_items_metricDataRepository_kind"></a>20.1.2.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository > kind</strong>  

</summary>
<blockquote>

|              |                    |
| ------------ | ------------------ |
| **Type**     | `enum (of string)` |
| **Required** | Yes                |

Must be one of:
* "influxdb"
* "prometheus"
* "cc-metric-store"
* "test"

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_metricDataRepository_url"></a>20.1.2.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository > url</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_metricDataRepository_token"></a>20.1.2.3. [Optional] Property cc-backend configuration file schema > clusters > clusters items > metricDataRepository > token</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_filterRanges"></a>20.1.3. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** This option controls the slider ranges for the UI controls of numNodes, duration, and startTime.

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_numNodes"></a>20.1.3.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > numNodes</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** UI slider range for number of nodes

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_numNodes_from"></a>20.1.3.1.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > numNodes > from</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_numNodes_to"></a>20.1.3.1.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > numNodes > to</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_duration"></a>20.1.3.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > duration</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** UI slider range for duration

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_duration_from"></a>20.1.3.2.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > duration > from</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_duration_to"></a>20.1.3.2.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > duration > to</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_startTime"></a>20.1.3.3. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > startTime</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | Yes                                                                       |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** UI slider range for start time

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_startTime_from"></a>20.1.3.3.1. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > startTime > from</strong>  

</summary>
<blockquote>

|              |             |
| ------------ | ----------- |
| **Type**     | `string`    |
| **Required** | Yes         |
| **Format**   | `date-time` |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="clusters_items_filterRanges_startTime_to"></a>20.1.3.3.2. [Required] Property cc-backend configuration file schema > clusters > clusters items > filterRanges > startTime > to</strong>  

</summary>
<blockquote>

|              |        |
| ------------ | ------ |
| **Type**     | `null` |
| **Required** | Yes    |

</blockquote>
</details>

</blockquote>
</details>

</blockquote>
</details>

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults"></a>21. [Optional] Property cc-backend configuration file schema > ui-defaults</strong>  

</summary>
<blockquote>

|                           |                                                                           |
| ------------------------- | ------------------------------------------------------------------------- |
| **Type**                  | `object`                                                                  |
| **Required**              | No                                                                        |
| **Additional properties** | [[Any type: allowed]](# "Additional Properties of any type are allowed.") |

**Description:** Default configuration for web UI

<details>
<summary>
<strong> <a name="ui-defaults_plot_general_colorBackground"></a>21.1. [Required] Property cc-backend configuration file schema > ui-defaults > plot_general_colorBackground</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | Yes       |

**Description:** Color plot background according to job average threshold limits

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_general_lineWidth"></a>21.2. [Required] Property cc-backend configuration file schema > ui-defaults > plot_general_lineWidth</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

**Description:** Initial linewidth

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_list_jobsPerPage"></a>21.3. [Required] Property cc-backend configuration file schema > ui-defaults > plot_list_jobsPerPage</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

**Description:** Jobs shown per page in job lists

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_view_plotsPerRow"></a>21.4. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_plotsPerRow</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `integer` |
| **Required** | Yes       |

**Description:** Number of plots per row in single job view

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_view_showPolarplot"></a>21.5. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_showPolarplot</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | Yes       |

**Description:** Option to toggle polar plot in single job view

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_view_showRoofline"></a>21.6. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_showRoofline</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | Yes       |

**Description:** Option to toggle roofline plot in single job view

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_view_showStatTable"></a>21.7. [Required] Property cc-backend configuration file schema > ui-defaults > plot_view_showStatTable</strong>  

</summary>
<blockquote>

|              |           |
| ------------ | --------- |
| **Type**     | `boolean` |
| **Required** | Yes       |

**Description:** Option to toggle the node statistic table in single job view

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_system_view_selectedMetric"></a>21.8. [Required] Property cc-backend configuration file schema > ui-defaults > system_view_selectedMetric</strong>  

</summary>
<blockquote>

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | Yes      |

**Description:** Initial metric shown in system view

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_analysis_view_histogramMetrics"></a>21.9. [Required] Property cc-backend configuration file schema > ui-defaults > analysis_view_histogramMetrics</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

**Description:** Metrics to show as job count histograms in analysis view

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                                           | Description |
| ----------------------------------------------------------------------------------------- | ----------- |
| [analysis_view_histogramMetrics items](#ui-defaults_analysis_view_histogramMetrics_items) | -           |

#### <a name="autogenerated_heading_3"></a>21.9.1. cc-backend configuration file schema > ui-defaults > analysis_view_histogramMetrics > analysis_view_histogramMetrics items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_analysis_view_scatterPlotMetrics"></a>21.10. [Required] Property cc-backend configuration file schema > ui-defaults > analysis_view_scatterPlotMetrics</strong>  

</summary>
<blockquote>

|              |                  |
| ------------ | ---------------- |
| **Type**     | `array of array` |
| **Required** | Yes              |

**Description:** Initial scatter plto configuration in analysis view

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                                               | Description |
| --------------------------------------------------------------------------------------------- | ----------- |
| [analysis_view_scatterPlotMetrics items](#ui-defaults_analysis_view_scatterPlotMetrics_items) | -           |

#### <a name="autogenerated_heading_4"></a>21.10.1. cc-backend configuration file schema > ui-defaults > analysis_view_scatterPlotMetrics > analysis_view_scatterPlotMetrics items

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | No                |

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | 1                  |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                                                           | Description |
| --------------------------------------------------------------------------------------------------------- | ----------- |
| [analysis_view_scatterPlotMetrics items items](#ui-defaults_analysis_view_scatterPlotMetrics_items_items) | -           |

##### <a name="autogenerated_heading_5"></a>21.10.1.1. cc-backend configuration file schema > ui-defaults > analysis_view_scatterPlotMetrics > analysis_view_scatterPlotMetrics items > analysis_view_scatterPlotMetrics items items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_job_view_nodestats_selectedMetrics"></a>21.11. [Required] Property cc-backend configuration file schema > ui-defaults > job_view_nodestats_selectedMetrics</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

**Description:** Initial metrics shown in node statistics table of single job view

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                                                   | Description |
| ------------------------------------------------------------------------------------------------- | ----------- |
| [job_view_nodestats_selectedMetrics items](#ui-defaults_job_view_nodestats_selectedMetrics_items) | -           |

#### <a name="autogenerated_heading_6"></a>21.11.1. cc-backend configuration file schema > ui-defaults > job_view_nodestats_selectedMetrics > job_view_nodestats_selectedMetrics items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_job_view_polarPlotMetrics"></a>21.12. [Required] Property cc-backend configuration file schema > ui-defaults > job_view_polarPlotMetrics</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

**Description:** Metrics shown in polar plot of single job view

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                                 | Description |
| ------------------------------------------------------------------------------- | ----------- |
| [job_view_polarPlotMetrics items](#ui-defaults_job_view_polarPlotMetrics_items) | -           |

#### <a name="autogenerated_heading_7"></a>21.12.1. cc-backend configuration file schema > ui-defaults > job_view_polarPlotMetrics > job_view_polarPlotMetrics items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_job_view_selectedMetrics"></a>21.13. [Required] Property cc-backend configuration file schema > ui-defaults > job_view_selectedMetrics</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                               | Description |
| ----------------------------------------------------------------------------- | ----------- |
| [job_view_selectedMetrics items](#ui-defaults_job_view_selectedMetrics_items) | -           |

#### <a name="autogenerated_heading_8"></a>21.13.1. cc-backend configuration file schema > ui-defaults > job_view_selectedMetrics > job_view_selectedMetrics items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_general_colorscheme"></a>21.14. [Required] Property cc-backend configuration file schema > ui-defaults > plot_general_colorscheme</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

**Description:** Initial color scheme

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                               | Description |
| ----------------------------------------------------------------------------- | ----------- |
| [plot_general_colorscheme items](#ui-defaults_plot_general_colorscheme_items) | -           |

#### <a name="autogenerated_heading_9"></a>21.14.1. cc-backend configuration file schema > ui-defaults > plot_general_colorscheme > plot_general_colorscheme items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

<details>
<summary>
<strong> <a name="ui-defaults_plot_list_selectedMetrics"></a>21.15. [Required] Property cc-backend configuration file schema > ui-defaults > plot_list_selectedMetrics</strong>  

</summary>
<blockquote>

|              |                   |
| ------------ | ----------------- |
| **Type**     | `array of string` |
| **Required** | Yes               |

**Description:** Initial metric plots shown in jobs lists

|                      | Array restrictions |
| -------------------- | ------------------ |
| **Min items**        | N/A                |
| **Max items**        | N/A                |
| **Items unicity**    | False              |
| **Additional items** | False              |
| **Tuple validation** | See below          |

| Each item of this array must be                                                 | Description |
| ------------------------------------------------------------------------------- | ----------- |
| [plot_list_selectedMetrics items](#ui-defaults_plot_list_selectedMetrics_items) | -           |

#### <a name="autogenerated_heading_10"></a>21.15.1. cc-backend configuration file schema > ui-defaults > plot_list_selectedMetrics > plot_list_selectedMetrics items

|              |          |
| ------------ | -------- |
| **Type**     | `string` |
| **Required** | No       |

</blockquote>
</details>

</blockquote>
</details>

----------------------------------------------------------------------------------------------------------------------------
Generated using [json-schema-for-humans](https://github.com/coveooss/json-schema-for-humans) on 2024-02-02 at 14:36:54 +0100