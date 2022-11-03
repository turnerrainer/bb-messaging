# 5 Cross-Cutting Requirements

{% hint style="success" %}
The Cross-cutting requirements described in this section are an extension of the cross-cutting requirements defined in the architecture blueprint and nonfunctional requirements document. This section will describe any additional cross-cutting requirements that apply to this building block.

Cross-cutting requirements will use the same language (MUST or SHOULD) as specified in the architecture document.
{% endhint %}

The Cross-cutting requirements described in this section are an extension of the cross-cutting requirements defined in the architecture specification document. This section will describe any additional cross-cutting requirements that apply to this building block.

Cross-cutting requirements will use the same language (MUST or SHOULD) as specified in the architecture document.

## 5.1 Denormalized databases MUST be used

There are 2 main reasons for usingdenormalized databases\[1] \[2] \[3]  instead of traditionalnormalized databases.

First, to significantly improve the performance of read queries. This is highly important as databases of Messaging BB will be under a heavy load of requests that in many cases are expected to respond near real-time.

Second, to be able to export the content of databases in the format of time-series databases (see below for its reasons).

To achieve this, using "UPDATE" and "DELETE" queries~~queires~~ in SQL commands SHOULD be disabled. If not, they MUST be avoided by developers and caught by automated tests is still used.

## **5.2 Content of production-level databases SHOULD be continuously archieved centrally**

By having this capability, it´s possible to delete the content of processed data from production-level servers databases right after they have been securely archived.

This is important to reduce the impact of potential data breachces by security incidents of potentially N number of application servers hosted by different parties.

## **5.3 Time-series databases SHOULD be convertable to ready-to-use relational databases and vice versa**

If done so, using archieved datasests, be it fully or partially, allows to recover and/or re-engineer lost databases (or just datasets of interests) automatically and in a matter of seconds if such pipelines have been predefined.

Also, by converting content of relational databases into a format of time-series databases, these purely text-based datasets are easily usable by different kind of databases, analytics tools etc, not just by the relational database used at first.

## **5.4 SHOULD enable message replication**

In order to prevent single points of failure, messages must be replicated on at least 2 different service providers.

In case of message replication, all unprocessed replicated messages MUST be kept track of and relevantly updated in order to prevent re-processing them.

## **5.5 MUST support policy configuration**

Admin of the room must be able to choose the policy profile with configuration of message provider, retrial frequency, e.g.

## **5.6** MUST support queuing mechanism

Unsent and unsuccessfully delivered messages must remain in a queue until being successfully delivered or otherwise permanently processed.

### **Messages Delivery Statuses:**

Pending: initial state for all messages waiting to be queued

Queued: messages that are in the queue to be sent

Sent: messages with proper confirmation that was sent to provider

Delivered: messages with proper confirmation that was delivered to the end-user

Errored: messages with error during delivery

Failed: messages that are errored and we gave up to send

### Delivery business rules:

Messages not delivered in a period of 24 hours: Any errored or queued messages more than 24 hours old must be labeled as failed and go out of the queue.

Messages retrial: Errored messages must be retried for 24 hours.

## 5.9 MUST follow OpenAPI annotations

A protocol describing the technical usage of any given or planned messaging types / platforms is mandatory.

Source code of applications must be covered with OpenAPI annotations.

Deployment of an application produces an updated version of publicly accessible Swagger UI in case technical specification has changed.

## **5.10 MUST use test-driven development**

All technical functionalities must be fully covered by automated tests.

## **5.11 All technical components MUST be stateless and horizontally scalable**

Regardless of the technical component, except relational databases, must be stateless in a sense of [https://en.wikipedia.org/wiki/Service\_statelessness\_principle](https://en.wikipedia.org/wiki/Service\_statelessness\_principle).

## **5.12 Databases SHOULD be horizontally scalable**

At least on the level of active-passive nodes based on the principle of "eventually consistent".

## **5.13 Messaging as a service MUST be vendor neutral**

If Messaging BB protocols are followed, the technical stack used to provide messaging as a service is vendor neutral, meaning that anyone is free to use technical solutions of their own choice.

## **5.14** Only allowed participants MUST be able to join the network

Only allowed participants are allowed to provide and use services of Messaging BB.

## 5.15 Central databases of users contacts and readable messages MUST NOT exist at Messaging BB

Messaging BB is a dumb messaging proxy which gets all of it´s relevant input from its clients. This also includes names and contact information of all relevant participants.

Such sensitive information may not exist in its raw and/or re-engineerable form neither in databases or logs.

## **5.16 Message content MUST be readable only by intended participants**

Depending on specific use case, this may mean

1. end-to-end encryption ([https://en.wikipedia.org/wiki/End-to-end\_encryption](https://en.wikipedia.org/wiki/End-to-end\_encryption)); or
2. SNI routing ([https://en.wikipedia.org/wiki/Server\_Name\_Indication](https://en.wikipedia.org/wiki/Server\_Name\_Indication)).

## **5.17 MUST support audit logging**

Every instance of a service must generate audit logs containing information about all of its actions regarding timestamps, related parties, identifiers to operations performed and HTTP response codes for any given action.

Audit logs may not contain actual content of the message.

Audit logs must be in a time series database format.

Audit logs must be accessible by a given endpoint by central service provider only.

Audit logs should be periodically removed from their original source after a defined period of time.

## **5.18 Cloud native is a MUST**

All stand-alone applications used and services created based upon them must be cloud-native in a sense of [https://en.wikipedia.org/wiki/Cloud\_native\_computing](https://en.wikipedia.org/wiki/Cloud\_native\_computing).

## **5.19** Source code MUST be published under a permissive license and be easily accessible by a public repository

Full source code of the building block must be published as easily accessible open source code.

All custom developments are published under the MIT License by default if not clearly stated otherwise.
