# XELERATE Front-End: Entity Labels

!!! info "Important"
    Labels are intended for use in conjunction with the XELERATE's new Front-end.

    Labels will *not be needed nor used* unless the new XELERATE Front-end is deployed.

    Please contact the XELERATE Development team for more details on the deployment of the new XELERATE Front-end.

Labels are created and maintained by the XELERATE admin team.

Labels are intended to match elements that are displayed as clickable search terms in the XELERATE Front-end. This includes information about the entity such as:

- Main Group
- Vehicle Platform
- Region
- Cloud Category
- On-Board Category
- Infotainment Category
- Data Category


## Labels: Details and Usage

To facilitate searchability and improve ease of discovery, XELERATE has adopted a fixed set of standardized **Labels** for content creators to use.

For each entity that you want displayed when a user is browsing and searching the XELERATE Front-end, you should add the appropriate labels as listed in the template below.


## Entity Template

```{.yaml linenums="1"}
---
apiVersion: backstage.io/v1alpha1
kind: System | Component | API
spec:
  owner:
  type: service | documentation | tool | signal
  lifecycle: in-development | production
  domain:  # Only used by "kind:System"
  system:  # Only used by "kind:Component & API"
metadata:
  name:
  title:
  description:
  annotations:  # Used for associating TechDocs with this entity
  tags:
    # Recommended Tags
    - cloud
    - edge
    - incar
    - data
    - ude
    - infotainment

    - vwac
    - ha
    - odp15
    - odp10

    - mod4
    - meb

    - developer-enablement
    - partner
    - security
    - azure
    - aws
  links:
    # See "XELERATE > Onboarding"
    - url: https://support.cariad.technology/foobar/support-center
      title: FooBar Support Center
      icon: help
  labels:
    # ONLY the following Labels are supported. Include if set to "true". Remove if not needed.
    cariad.technology/main-group.cloud: "true"
    cariad.technology/main-group.on-board: "true"
    cariad.technology/main-group.data: "true"
    cariad.technology/main-group.infotainment: "true"

    cariad.technology/vehicle-platform.j1: "true"
    cariad.technology/vehicle-platform.meb: "true"
    cariad.technology/vehicle-platform.mlb: "true"
    cariad.technology/vehicle-platform.mqb: "true"
    cariad.technology/vehicle-platform.msb: "true"
    cariad.technology/vehicle-platform.ppc: "true"
    cariad.technology/vehicle-platform.ppe: "true"
    cariad.technology/vehicle-platform.ssp: "true"

    cariad.technology/region.nar: "true"
    cariad.technology/region.eu: "true"
    cariad.technology/region.china: "true"
    cariad.technology/region.row: "true"

    cariad.technology/cloud-cat.adas: "true"
    cariad.technology/cloud-cat.config-specs: "true"
    cariad.technology/cloud-cat.dev-enablement: "true"
    cariad.technology/cloud-cat.evcharging: "true"
    cariad.technology/cloud-cat.fleet: "true"
    cariad.technology/cloud-cat.hvac: "true"
    cariad.technology/cloud-cat.nav: "true"
    cariad.technology/cloud-cat.user-info: "true"
    cariad.technology/cloud-cat.veh-alert: "true"
    cariad.technology/cloud-cat.veh-command-control: "true"
    cariad.technology/cloud-cat.veh-connectivity: "true"
    cariad.technology/cloud-cat.veh-telemetry: "true"

    cariad.technology/incar-cat.adas: "true"
    cariad.technology/incar-cat.accel: "true"
    cariad.technology/incar-cat.angular-vel: "true"
    cariad.technology/incar-cat.body: "true"
    cariad.technology/incar-cat.cabin: "true"
    cariad.technology/incar-cat.chassis: "true"
    cariad.technology/incar-cat.connectivity: "true"
    cariad.technology/incar-cat.current-loc: "true"
    cariad.technology/incar-cat.dev-enablement: "true"
    cariad.technology/incar-cat.driver: "true"
    cariad.technology/incar-cat.exterior: "true"
    cariad.technology/incar-cat.infotainment: "true"
    cariad.technology/incar-cat.obd: "true"
    cariad.technology/incar-cat.powertrain: "true"
    cariad.technology/incar-cat.service: "true"
    cariad.technology/incar-cat.trailer: "true"
    cariad.technology/incar-cat.veh-id: "true"

    cariad.technology/infotainment-cat.nav: "true"
    cariad.technology/infotainment-cat.payments: "true"
    cariad.technology/infotainment-cat.vehicle: "true"

    cariad.technology/data-cat.catalog: "true"
    cariad.technology/data-cat.consumption: "true"
    cariad.technology/data-cat.ingestion: "true"
    cariad.technology/data-cat.pipeline: "true"
    cariad.technology/data-cat.protection: "true"
    cariad.technology/data-cat.storage: "true"
    cariad.technology/data-cat.streaming: "true"
    cariad.technology/data-cat.transform: "true"
    cariad.technology/data-cat.troubleshoot: "true"
```
