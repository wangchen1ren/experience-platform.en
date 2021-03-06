---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Getting started
topic: API guide
---

# Identity Service API developer guide

Adobe Experience Platform Identity Service manages the cross-device, cross-channel, and near real-time identification of your customers in what is known as an identity graph within Adobe Experience Platform. 

## Getting started

This guide requires a working understanding of the following components of Adobe Experience Platform:

- [Identity Service](../home.md): Solves the fundamental challenge posed by the fragmentation of customer profile data. It does this by bridging identities across devices and systems where customers interact with you brand.
- [Real-time Customer Profile](../../profile/home.md): Provides a unified, consumer profile in real-time based on aggregated data from multiple sources. 
- [Experience Data Model (XDM)](../../xdm/home.md): The standardized framework by which Platform organizes customer experience data.

The following sections provide additional information that you will need to know or have on-hand in order to successfully make calls to the Identity Service API.

### Reading sample API calls

This guide provides example API calls to demonstrate how to format your requests. These include paths, required headers, and properly formatted request payloads. Sample JSON returned in API responses is also provided. For information on the conventions used in documentation for sample API calls, see the section on [how to read example API calls](../../landing/troubleshooting.md#how-do-i-format-an-api-request) in the Experience Platform troubleshooting guide.

### Gather values for required headers

In order to make calls to Platform APIs, you must first complete the [authentication tutorial](../../tutorials/authentication.md). Completing the authentication tutorial provides the values for each of the required headers in all Experience Platform API calls, as shown below:

- Authorization: Bearer `{ACCESS_TOKEN}`
- x-api-key: `{API_KEY}`
- x-gw-ims-org-id: `{IMS_ORG}`

All resources in Experience Platform are isolated to specific virtual sandboxes. All requests to Platform APIs require a header that specifies the name of the sandbox the operation will take place in:

- x-sandbox-name: `{SANDBOX_NAME}`

>[!NOTE] For more information on sandboxes in Platform, see the [sandbox overview documentation](../../sandboxes/home.md).

All requests that contain a payload (POST, PUT, PATCH) require an additional header:

- Content-Type: application/json

### Region-based routing

The Identity Service API employs region-specific endpoints that require the inclusion of a `{REGION}` as part of the request path. During the provisioning of your IMS Organization, a region is determined and stored within your IMS Org profile. Using the correct region with each endpoint ensures that all requests made using the Identity Service API are routed to the appropriate region. 

There are two regions currently supported by Identity Service APIs: VA7 and NLD2. 

The table below shows example paths using regions:

| Service | Region: VA7 | Region: NLD2 |
| ------ | -------- |--------- |
| Identity Service API | https://</span>platform-va7.adobe.</span>io/data/core/identity/{ENDPOINT}|https://</span>platform-nld2.adobe.</span>io/data/core/identity/{ENDPOINT} |
| Identity Namespace API | https://</span>platform-va7.adobe.</span>io/data/core/idnamespace/{ENDPOINT}|https://</span>platform-nld2.adobe.</span>io/data/core/idnamespace{ENDPOINT} |

>[!NOTE] Requests made without specifying a region may result in calls routing to the incorrect region or cause calls to fail unexpectedly.

If you are unable to locate the region within your IMS Org profile, please contact your system administrator for support.

## Using the Identity Service API

Identity parameters used in these services can be expressed in one of two ways; composite or XID.

Composite identities are constructs including both the ID value and namespace. When using composite identities, the namespace can be supplied by either name (`namespace.code`) or ID (`namespace.id`).

When an identity is persisted, Identity Service generates and assigns an ID to that identity, called the native ID, or XID. All variations of Cluster and Mapping APIs support both composite identities and XID in their requests and response. One of the parameters is required - `xid` or combination of [`ns` or `nsid`] and `id` to use these APIs.

To limit the payload in responses, APIs adapt their responses to the type of identity construct used. That is, if you pass XID your responses will have XIDs, if you pass composite identities, the response will follow the structure used in the request.

The examples in this document do not cover the complete functionality of the Identity Service API. For the complete API, see the [Swagger API Reference](https://www.adobe.io/apis/experienceplatform/home/api-reference.html#!acpdr/swagger-specs/id-service-api.yaml).

>[!NOTE] All identities returned will be in native XID form when native XID is used in the request. Using the ID/namespace form is recommended. For more information, see the section on [getting the XID for an identity](./create-custom-namespace.md).

## Next steps

Now that you have gathered the required credentials, you can now continue to read the rest of the developer guide. Each section provides important information regarding their endpoints and demonstrate example API calls for performing CRUD operations. Each call includes the general **API format**, a sample **request** showing required headers and properly formatted payloads, and a sample **response** for a successful call.
