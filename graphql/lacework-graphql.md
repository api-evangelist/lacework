# Lacework FortiCNAPP GraphQL Schema

## Overview

This document describes a conceptual GraphQL schema for the Lacework FortiCNAPP platform. Lacework (now Lacework FortiCNAPP under Fortinet) is a cloud-native application protection platform (CNAPP) that delivers vulnerability management, compliance, threat detection, posture management, and workload protection across AWS, Azure, GCP, Kubernetes, and containers.

The Lacework FortiCNAPP REST API is the authoritative interface. This GraphQL schema is a conceptual representation derived from the REST API surface documented at https://docs.lacework.net/api/ and https://docs.fortinet.com/document/lacework-forticnapp/latest/api-reference.

## Schema Source

- REST API Reference: https://docs.fortinet.com/document/lacework-forticnapp/latest/api-reference/863111/about-the-lacework-forticnapp-api
- OpenAPI Spec: https://api.lacework.net/api/v2/docs/lacework-api-v2.0.yaml
- Authentication: Bearer token via /api/v2/access/tokens

## Authentication

All queries and mutations require a Bearer access token obtained from API keys via the `/api/v2/access/tokens` endpoint. The token is scoped to the tenant and account identified by the subdomain (`YourAccount.lacework.net`).

## Core Domain Areas

### Vulnerabilities

Vulnerabilities cover CVEs discovered in hosts, containers, and packages. The schema exposes `Vulnerability`, `VulnerabilityDetails`, `CVE`, `Severity`, `CVSS`, `FixAvailable`, and `AffectedPackage` types. Queries allow filtering by severity, fix availability, container image, host, and time range.

### Containers

Container types model running workloads and their images. Types include `Container`, `ContainerDetails`, `ContainerImage`, `ContainerRegistry`, and `ImageLayer`. Containers are linked to their host, cloud account, and associated vulnerabilities.

### Hosts and Cloud Instances

Host and cloud types cover compute assets. `Host`, `HostDetails`, `CloudInstance`, and `CloudAccount` model the compute layer. Hosts carry agent data, network connections, and process behaviors.

### Compliance

Compliance types represent policy frameworks evaluated against cloud resources. Types include `Compliance`, `ComplianceReport`, `CompliancePolicy`, `ComplianceRecommendation`, and `ComplianceSummary`. Reports are scoped to accounts and cloud providers.

### Alerts

Alerts are the primary signal surface in Lacework. The schema models `Alert`, `AlertSeverity`, `AlertSource`, `AlertEvent`, and specialized subtypes: `PolicyAlert`, `ComplianceAlert`, `BehaviorAlert`, `AnomalyAlert`, and `AttackEvent`. Alerts link to their source events, affected resources, and threat intelligence.

### Threats and Cloud Activity

`Threat`, `ThreatIntelligence`, `CloudTrailEvent`, `AuditLog`, `CloudActivity`, `ActivityCategory`, and `ActivityType` model detected threats and the audit trail of cloud API calls.

### Resources

`Resource`, `ResourceDetails`, `ResourceTag`, and `ResourcePolicy` model cloud assets inventoried by Lacework across AWS, Azure, GCP, and Kubernetes.

### IAM and Users

Identity types include `User`, `UserDetails`, `IAMUser`, `IAMRole`, `IAMPolicy`, `Group`, and `Permission`. These represent both Lacework platform users and cloud identity entities.

### Agents and Network

`AgentData`, `AgentHealth`, and `AgentVersion` model the Lacework agent deployed on hosts. `Network`, `NetworkConnection`, `NetworkPort`, and `NetworkProtocol` model observed network activity. `Process` and `ProcessBehavior` model running processes and behavioral anomalies.

### Integrations and Configuration

`IntegrationConfig`, `Webhook`, `APIKey`, `Token`, and `APIContext` model platform configuration and external integrations.

## Named Types (55+)

See `lacework-schema.graphql` for the full schema definition.

The schema defines the following named types:

1. Vulnerability
2. VulnerabilityDetails
3. CVE
4. Severity
5. CVSS
6. FixAvailable
7. AffectedPackage
8. Container
9. ContainerDetails
10. ContainerImage
11. ContainerRegistry
12. ImageLayer
13. Host
14. HostDetails
15. CloudInstance
16. CloudAccount
17. Compliance
18. ComplianceReport
19. CompliancePolicy
20. ComplianceRecommendation
21. ComplianceSummary
22. Alert
23. AlertSeverity
24. AlertSource
25. AlertEvent
26. PolicyAlert
27. ComplianceAlert
28. BehaviorAlert
29. AnomalyAlert
30. AttackEvent
31. Threat
32. ThreatIntelligence
33. CloudTrailEvent
34. AuditLog
35. CloudActivity
36. ActivityCategory
37. ActivityType
38. Resource
39. ResourceDetails
40. ResourceTag
41. ResourcePolicy
42. User
43. UserDetails
44. IAMUser
45. IAMRole
46. IAMPolicy
47. Group
48. Permission
49. APIContext
50. AgentData
51. AgentHealth
52. AgentVersion
53. Network
54. NetworkConnection
55. NetworkPort
56. NetworkProtocol
57. Process
58. ProcessBehavior
59. IntegrationConfig
60. Webhook
61. APIKey
62. Token
63. Query
64. Mutation
