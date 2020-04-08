---

copyright:

  years: 2017, 2020

lastupdated: "2020-04-08"

keywords: crn, cloud resource name, resources, cloud catalog

subcollection: resources

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# Cloud Resource Names
{: #crn}

Cloud Resource Names (CRNs) uniquely identify {{site.data.keyword.Bluemix_notm}} resources. A CRN is used to specify a resource in an unambiguous way that is guaranteed to be globally unique. The same as {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) policies and services that are listed in the cloud catalog.

A CRN is formed from a concatenation of "segments" that hierarchically identify the resource, its location, and the service it belongs to. The segment delimiter is set to ':' (the colon character). All CRNs begin with the segment identifier `crn`.


## CRN format
{: #format-crn}

The base canonical format of a CRN is:

`crn:version:cname:ctype:service-name:location:scope:service-instance:resource-type:resource`


## version
{: #version-crn}

The `version` segment identifies the version of the CRN format. Currently, the only valid version segment value is `v1`.


## cname
{: #cname-crn}

The `cname` segment identifies the cloud instance and is an alphanumeric identifier that uniquely identifies the cloud instance that contains the resource. A `cname` effectively identifies an independent control plane that owns the identified resource. The value for the `cname` segment must be `bluemix` for {{site.data.keyword.Bluemix_notm}} users.


## ctype
{: #ctype-crn}

The `ctype` segment identifies the type of cloud instance that is represented by the specified `cname` segment.

 Valid values:
  - `public`: All services that are available from the public catalog
  - `dedicated`: Only for current {{site.data.keyword.Bluemix_notm}} dedicated environments
  - `local`: All services that are deployed locally in your own environment


## service-name
{: #service-name-crn}

The `service-name` segment uniquely identifies a capability (service, component, product) being offered by the cloud. The capability can be a user-provided service, such as with the services that are listed in the {{site.data.keyword.Bluemix_notm}} catalog, or an internal architectural component critical to the {{site.data.keyword.Bluemix_notm}} functionality.

The `service-name` segment indicates the service that the resource belongs to, and {{site.data.keyword.Bluemix_notm}} enforces global uniqueness of service names. The `service-name` segment must be alphanumeric, lowercase, and no spaces or special characters other than '-'.

For services that are registered into the {{site.data.keyword.Bluemix_notm}} catalog the `service-name` segment must correspond to one of the services that are registered to the {{site.data.keyword.Bluemix_notm}} Global Catalog service. It is the `name` property that is returned by the {{site.data.keyword.Bluemix_notm}} Global Catalog service API `GET https://globalcatalog.cloud.ibm.com/api/v1/{id}` for the corresponding resource instance or the `service-name` value that is displayed by the command-line interface (CLI): `ibmcloud service offerings` in the column `service`.


## location
{: #location-crn}

The cloud geography/region/zone/data center that the resource resides.

The `location` segment must be one of the following values:

### Global
{: #global-crn}

 * `global`

### Geographies
{: #geos-crn}

 * `us`
 * `eu`
 * `cn`
 * `ap`

### Regions
{: #regions-crn}

 * `us-south`
 * `us-east`
 * `au-syd`
 * `eu-gb`
 * `eu-de`
 * `jp-tok`

### Data centers
{: #dc-crn}

 * `AMS01`
 * `AMS03`
 * `CHE01`
 * `DAL01`
 * `DAL05`
 * `DAL06`
 * `DAL07`
 * `DAL09`
 * `DAL10`
 * `DAL12`
 * `DAL13`
 * `FRA02`
 * `HKG02`
 * `HOU02`
 * `LON02`
 * `MEL01`
 * `MEX01`
 * `MIL01`
 * `MON01`
 * `OSL01`
 * `PAR01`
 * `SJC01`
 * `SJC03`
 * `SAO01`
 * `SEA01`
 * `SEO01`
 * `SNG01`
 * `SYD01`
 * `TOK02`
 * `TOR01`
 * `WDC01`
 * `WDC04`
 * `WDC06`
 * `WDC07`

Some resources do not require a region, as they can be considered global. In this case, the `region` segment is set to `global`.
{: tip}


## scope
{: #scope-crn}

The `scope` segment identifies the containment or owner of the resource. Some resources do not require an owner (they can be considered `global`). In this case, the `scope` segment is empty (a blank string).

The value of the `scope` segment must be formatted as `{scopePrefix}`/`{id}`. The `scopePrefix` represents the format that is used to identify the owner or containment. The `id` represents the identity of the owner or containment in a format that is specific to the `scopePrefix`.

| Scope Type   | Scope Prefix     | Usage                                                                                   | Example                                  |
|--------------|------------------|-----------------------------------------------------------------------------------------|------------------------------------------|
| Account      | a/`{account id}` | The account that the resource was created in.                                           | `a/292558`                               |
| Organization | o/`{org guid}`   | The {{site.data.keyword.Bluemix_notm}} Organization to which the resource was assigned. | `o/4716e2d1-35b7-431f-891a-b552bf0b3c66` |
| Space        | s/`{space guid}` | The {{site.data.keyword.Bluemix_notm}} Space to which the resource was assigned.        | `s/48b3cdcd-e804-4398-9032-73065863ad7c` |
{: caption="Table 1. `scope` usage" caption-side="top"}


## service-instance
{: #service-instance-crn}

The `service-instance` segment identifies the service instance uniquely. The format of the `service-instance` segment varies by service. Each service must document the format of their `service_instance` segment as part of their service metadata. Some services do not have instances because the instance is global, and in this case the `service-instance` field is blank.

The `service-instance` must be alphanumeric, lowercase, no spaces, or special characters other than '-' and '/'.

For example, a DevOps tool that is used to track and plan work items can have a simple `GUID` instance ID ("1234-5678-9012-3456"). But, the policy component of an autoscale group service can use a hierarchical naming convention and have a `service-id` segment of:

>`c7a27f55-d35e-4153-b044-8ca9155fc467/my-test-asg1/my-scaleout-policy`

You can also obtain a CRN from an {{site.data.keyword.Bluemix_notm}} resource by using the following CLI command:
```
ibmcloud resource service-instance
```
{: codeblock}

## resource-type, resource
{: #resource-type-crn}

The values of the `resource-type` and `resource` segments vary by service. A service is required to document their supported `resource types` segment and the format of the `resource` segment as part of their service metadata.

As an example, an image in the customer receipts container in an Object Storage service can have a `resource-type` segment of  `object` and a `resource` value of `CustomerReceipts/clientdinner.png`.

The `resource-type` segment must be alphanumeric, lowercase, and no spaces or special characters other than '-'. A service can decide that the `resource-type` segment is optional, in which case it is left blank.


## CRN examples
{: #crn_examples}

The following table provides a list of CRN examples.

| Example           | Value |
|-------------------|-------|
| Kubernetes Worker | `crn:v1:bluemix:public:containers-kubernetes:us-south:a/59bcbfa6ea2f006b4ed7094c1a08dcdd:8042b2a8af6a4a5cbf6dbe09e07311d2:worker:kube-hou02-pa8042b2a8af6a4a5cbf6dbe09e07311d2-w1` |
| Resource Group    | `crn:v1:bluemix:public:resource-controller: global:a/59bcbfa6ea2f006b4ed7094c1a08dcdd:resource-group:59bcbfa6ea2f006b4ed7094c1a08dcdd` |
| Service Instance  | `crn:v1:bluemix:public:cloud-object-storage:global:a/59bcbfa6ea2f006b4ed7094c1a08dcdd:1a0ec336-f391-4091-a6fb-5e084a4c56f4::` |
| Bucket            | `crn:v1:bluemix:public:cloud-object-storage:global:a/59bcbfa6ea2f006b4ed7094c1a08dcdd:1a0ec336-f391-4091-a6fb-5e084a4c56f4:bucket:mybucket` |
{: caption="Table 2. CRN examples" caption-side="top"}
