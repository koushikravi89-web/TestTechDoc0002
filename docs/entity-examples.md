Below find entity examples from the ACBU Data Platform team. These can be used as representative blueprints for you to copy, clone, borrow, and learn from.

View this **ACBU Data Platform** System in the XELERATE Software Catalog at:https://developer.cariad.digital/catalog/default/system/vwac-data

## Term Clarification

| Term        | Usage Recommendation |
|-------------|----------------------|
| `kind`      | Use `System` if your entity is providing a service to CARIAD. <br> Use `Component` if you are simply publishing documentation. <br> Use `API` for any supported API including: OpenAPI, AsyncAPI, GraphQL, or gRPC. <br> **Note:** The value of `kind` is the only setting where capitalization matters.
| `tags`      | Tags are user-defined and should be short. Only four or fewer tags should be assigned to any entity. They should indicate a few primary search terms that a consumer might use to help find your entity. Keep in mind that Title, Description, and Tag content are all searchable in XELERATE.
| `links`     | These will display on the entity's **Overview** tab within XELERATE.
| `lifecycle` | Use `in-development` until the appropriate time to change to `production`.
| `domain`    | (Optional) Only the `kind: System` entity can reference a Domain. Domains are created and managed by the XELERATE Admin team. The current list of Domains can be found in the [XELERATE Catalog](https://developer.cariad.digital/catalog?filters%5Bkind%5D=domain&filters%5Buser%5D=all) and are listed below: <br> - `device-platform` <br> - `service-platform` <br> - `in-car` <br> - `ude` (i.e., "data")
| `labels`    | Labels are created and maintained by the XELERATE Admin team. <br> Labels are intended to match elements that are displayed as clickable search terms in XELERATE's new Front-end. <br> This includes information about the entity such as: <br> - Main Group <br> - Vehicle Platform <br> - Region <br> - Cloud Category <br> - On-Board Category <br> - Infotainment Category <br> - Data Category <br> See the [Entity Labels](./entity-labels.md) article for more information on labels.


## Example: `catalog-info-acbu-data-platform.yml`

```{.yaml linenums="1"}

##############################################################
# TEAM:    ACBU Data Platform
# ENTITY:  kind: System, type: service
# CONTACT: (add names and emails here)
##############################################################

---
apiVersion: backstage.io/v1alpha1
kind: System
spec:
  type: service
  owner: acbu-owners
  domain: ude
  lifecycle: production
metadata:
  name: vwac-data
  title: "ACBU: Data Platform"
  description: ACBU's Data Platform enables customers to create data ingestion flows that receive device telemetry from a connected vehicle and then validate, transform, and store the data in a repository so that the telemetry content can be extracted and/or consumed by an end-user's analytics, visualization, database, or reporting tools.
  annotations:
    backstage.io/techdocs-ref: dir:.
  tags:
    - vwac
    - cloud
    - edge
    - data
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url: mailto:jane.doe@cariad.us
      title: Jane Doe, Sr. Mgr., Product Management
      icon: email
    - url:https://developer.cariad.digital/catalog/default/system/vwac
      title: ACBU Connected Vehicle Platform & APIs
      icon: catalog
    - url:https://developer.cariad.digital/catalog/default/component/vdc/docs
      title: Vehicle Data Catalog (VDC) Documentation
      icon: docs
    labels:
    cariad.technology/main-group.data: "true"
    cariad.technology/type.api: "true"
    cariad.technology/type.use-case: "true"
    cariad.technology/type.service: "true"
    cariad.technology/type.guide: "true"
    cariad.technology/type.tool: "true"
    cariad.technology/vehicle-platform.j1: "true"
    cariad.technology/vehicle-platform.meb: "true"
    cariad.technology/vehicle-platform.mlb: "true"
    cariad.technology/vehicle-platform.mqb: "true"
    cariad.technology/vehicle-platform.msb: "true"
    cariad.technology/vehicle-platform.ppc: "true"
    cariad.technology/vehicle-platform.ppe: "true"
    cariad.technology/region.nar: "true"
    cariad.technology/region.eu: "true"
    cariad.technology/region.china: "true"
    cariad.technology/data-cat.catalog: "true"
    cariad.technology/data-cat.consumption: "true"
    cariad.technology/data-cat.ingestion: "true"
    cariad.technology/data-cat.pipeline: "true"
    cariad.technology/data-cat.protection: "true"
    cariad.technology/data-cat.storage: "true"
    cariad.technology/data-cat.streaming: "true"
    cariad.technology/data-cat.transform: "true"
    cariad.technology/data-cat.troubleshoot: "true"


##############################################################
# Data Platform: Group 1
# Team: Galaxy
# PO: (contact name, email here))
##############################################################

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/dataprotection-V2.json
metadata:
  name: acbu-data-platform-data-protection
  title: Data Platform Data Protection API, v2
  tags:
    - data
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/fileuploadservice-V1.json
metadata:
  name: acbu-data-platform-file-upload-service
  title: Data Platform File Upload Service API, v1
  tags:
    - data
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/datapingestion-V1.json
metadata:
  name: acbu-data-platform-ingestion-api
  title: Data Platform Ingestion API, v1
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/dataplatform-V2.json
metadata:
  name: acbu-data-platform-management
  title: Data Platform Management API, v2
  tags:
    - data
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/messageconverter-V1.json
metadata:
  name: acbu-data-platform-message-converter
  title: Data Platform Message Converter API, v1
  tags:
    - data
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard



##############################################################
# Data Platform: Group 2
# Team: Constellation
# PO: (contact name, email here))
##############################################################

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/datapworkbench-V1.json
metadata:
  name: acbu-data-platform-workbench
  title: Data Platform Workbench API, v1
  tags:
    - data
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard



##############################################################
# Data Platform Group 3
# Team: Accelerator
# PO: (contact name, email here))
##############################################################

# ------------------------------------------------------------
# COMPONENT: MDC/VDC API
# ------------------------------------------------------------

---
apiVersion: backstage.io/v1alpha1
kind: Component
spec:
  type: service
  owner: vdc-owners
  system: vwac-data
  lifecycle: production
  providesApis:
    - acbu-mdc-service
    - acbu-mdc-signal-sensitivity-service
    # - acbu-data-platform-mdc-service ## Attempted to rename for consistency sake but that broke Release Note Publishing. Restoring Orig. Name!
    # - acbu-data-platform-mdc-signal-sensitivity-service
metadata:
  name: vdc
  title: Vehicle Data Catalog
  description: The Vehicle Data Catalog (VDC) is the repository for all telemetry signals across all VW brands.
  annotations:
    backstage.io/techdocs-ref: dir:.
  tags:
    - cloud
    - data
    - vwac
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard
    - url: mailto:jose.doe@cariad.us
      title: "Team Lead/Email: Jose Doe"
      icon: email
  labels:
    cariad.technology/main-group.data: "true"
    cariad.technology/type.api: "true"
    cariad.technology/type.service: "true"
    cariad.technology/type.guide: "true"
    cariad.technology/vehicle-platform.ppc: "true"
    cariad.technology/vehicle-platform.ppe: "true"
    cariad.technology/region.nar: "true"
    cariad.technology/region.eu: "true"
    cariad.technology/region.china: "true"
    cariad.technology/data-cat.catalog: "true"
    cariad.technology/data-cat.protection: "true"

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: vdc-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/mdc-V1.json
metadata:
  name: acbu-mdc-service
  title: MDC Service API, v1
  description: The Vehicle Data Catalog (VDC/MDC) API is used to query the Master Data Catalog and retrieve telemetry signal definition.
  tags:
    - cloud
    - data
    - vwac
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url:https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard
    - url: mailto:jose.doe@cariad.us
      title: "Team Lead/Email: Jose Doe"
      icon: email
  labels:
    cariad.technology/main-group.data: "true"
    cariad.technology/type.api: "true"
    cariad.technology/vehicle-platform.ppe: "true"
    cariad.technology/region.nar: "true"
    cariad.technology/region.eu: "true"
    cariad.technology/region.china: "true"
    cariad.technology/data-cat.catalog: "true"
    cariad.technology/data-cat.protection: "true"

---
apiVersion: backstage.io/v1alpha1
kind: API
spec:
  type: openapi
  owner: vdc-owners
  system: vwac-data
  lifecycle: production
  definition:
    $text: ./apis/mdc-signal-sensitivity-V1.json
metadata:
  name: acbu-mdc-signal-sensitivity-service
  title: MDC Signal Sensitivity Service API, v1
  tags:
    - cloud
    - data
    - vwac
  links:
    - url: https://developer.vwcloud.io/s/support-center
      title: ACBU Support Center
      icon: help
    - url: https://developer.cariad.digital/catalog/default/system/data-platform
      title: ACBU Data Platform (System)
      icon: dashboard
    - url: mailto:jose.doe@cariad.us
      title: "Team Lead/Email: Jose Doe"
      icon: email
  labels:
    cariad.technology/main-group.data: "true"
    cariad.technology/type.api: "true"
    cariad.technology/vehicle-platform.ppe: "true"
    cariad.technology/region.nar: "true"
    cariad.technology/region.eu: "true"
    cariad.technology/region.china: "true"
    cariad.technology/data-cat.catalog: "true"
    cariad.technology/data-cat.protection: "true"



##############################################################
# Data Platform: Related Entities / T4 Components
##############################################################

---
apiVersion: backstage.io/v1alpha1
kind: Component
spec:
  type: website
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
metadata:
  name: dcom
  title: Data Collection Order Management (DCOM)
  description: "Group Data Collector's (GDC) Data Collection Order Management (DCOM) is the web tool used to order data to be collected from vehicles and sent to the Data Platform for consumption and/or storage."
  tags:
    - cloud
    - edge
    - vwac
    - in-vehicle
    - data-platform
  links:
    - url: https://022.appr.dcom.nar.gdc.vwautocloud.net/
      title: DCOM NAR Approval
      icon: catalog
    - url: https://018.appr.dcom.eu.gdc.vwautocloud.net/
      title: DCOM EU Approval
      icon: catalog
    - url: https://appr.dcom.cn.gdc.vwautocloud.cn/
      title: DCOM CN Approval
      icon: catalog
    - url: https://017.tui.dcom.eu.gdc.vwautocloud.net/
      title: DCOM INT
      icon: catalog

---
apiVersion: backstage.io/v1alpha1
kind: Component
spec:
  type: website
  owner: vdc-owners
  system: vwac-data
  lifecycle: production
metadata:
  name: vdc-signal
  title: VDC Signal Control
  description: "The VDC is the library of all the signals generated by components in vehicles. The VDC is used to decode and normalize the signal data as it is ingested into the Data Platform. The VDC is also used for regional sensitivity tracking of individual signals, such that highly sensitive signals are sent to the correct processing environment."
  tags:
    - cloud
    - edge
    - vwac
    - in-vehicle
    - data-platform
  links:
    - url: https://int-mdcv-d6f-mdcsignalsensitivityui-as.azurewebsites.net
      title: VDC Signal Sensitivity INT
      icon: catalog
  labels:
    cariad.technology/main-group.on-board: "true"
    cariad.technology/main-group.data: "true"
    cariad.technology/type.service: "true"
    cariad.technology/type.signal: "true"
    cariad.technology/vehicle-platform.j1: "true"
    cariad.technology/vehicle-platform.meb: "true"
    cariad.technology/vehicle-platform.mlb: "true"
    cariad.technology/vehicle-platform.mqb: "true"
    cariad.technology/vehicle-platform.msb: "true"
    cariad.technology/vehicle-platform.ppc: "true"
    cariad.technology/vehicle-platform.ppe: "true"
    cariad.technology/device-platform.ha: "true"
    cariad.technology/device-platform.odp1.0: "true"
    cariad.technology/device-platform.odp1.5: "true"
    cariad.technology/region.nar: "true"
    cariad.technology/region.eu: "true"
    cariad.technology/region.china: "true"
    cariad.technology/signal-cat.adas: "true"
    cariad.technology/signal-cat.accel: "true"
    cariad.technology/signal-cat.angular-vel: "true"
    cariad.technology/signal-cat.body: "true"
    cariad.technology/signal-cat.cabin: "true"
    cariad.technology/signal-cat.chassis: "true"
    cariad.technology/signal-cat.connectivity: "true"
    cariad.technology/signal-cat.current-loc: "true"
    cariad.technology/signal-cat.dev-enablement: "true"
    cariad.technology/signal-cat.driver: "true"
    cariad.technology/signal-cat.exterior: "true"
    cariad.technology/signal-cat.infotainment: "true"
    cariad.technology/signal-cat.obd: "true"
    cariad.technology/signal-cat.powertrain: "true"
    cariad.technology/signal-cat.service: "true"
    cariad.technology/signal-cat.trailer: "true"
    cariad.technology/signal-cat.veh-id: "true"
    cariad.technology/data-cat.consumption: "true"
    cariad.technology/data-cat.ingestion: "true"
    cariad.technology/data-cat.transform: "true"

---
apiVersion: backstage.io/v1alpha1
kind: Component
spec:
  type: website
  owner: acbu-owners
  system: vwac-data
  lifecycle: production
metadata:
  name: dp-grafana
  title: Data Platform Grafana Dashboard
  description: The Data Platform Grafana Dashboard shows performance of the Data Platform in the EU Production environment by Component and by Use Case. Displays include graphs showing counts of messages and response times.
  tags:
    - cloud
    - edge
    - vwac
    - in-vehicle
    - data-platform
  links:
    - url: https://cariadus.grafana.net/d/leu-strm-dta/live-eu-streaming-data?orgId=1
      title: Live EU Streaming Dashboard
      icon: catalog


##############################################################
# End of Data Platform content
##############################################################
```
