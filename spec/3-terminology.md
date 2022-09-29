# 3 Terminology



{% hint style="success" %}
Terminology/glossary used within the specification
{% endhint %}

## **Definition of the Message**

The message is the main entity of communication in this building block, it holds all the necessary information to deliver the information to the publisher or to the subscriber/client, leaving just a track of delivery logs with no personal data included. Messages follow a predefined protocol and policy for the chosen or predefined communication channel. As a rule, the delivery mode of the message is asynchronous.

## **Publisher**

This is the originator of the message, it holds the information about the content of the message and the (meta)data regarding the subscriber who will receive the message. In another words, Messaging BB proxies/relays the message received by a communication channel to the proper subscriber/client/person.

## **Subscriber**

In the Publish and Subscribe use case, where publisher is relaying the message into the hands of Messaging BB that will in turn route it to the desired communication channel, the subscriber is the one who is listening to the relevant Message Room to receive the message from a publisher. The subscriber has given the consent to the publisher to access or retrieve and store its data for the purpose of carrying out the messaging event.

## **Messaging event**

Messaging event is the (single) act of asynchronous information transfer between the publisher and subscriber, consisting of the following steps: 1) secure identification and access management of the publisher and subscriber; 2) access to and/or retrieval of relevant subscriber data and consent for using the data from the subscriber; 3) selection of relevant data transfer policy and protocol for the messaging event; 4) Management and processing of logs and relevant metadata during and after the messaging event.

## **Messaging protocol**

Is the protocol enabling the Messaging BB to communicate and transfer data between the endpoints.

NB! In its initial versions, GovStack Messaging BB is using [Matrix/Elements ](https://matrix.org/)protocol as a reference point for creating GovStack Messaging BB protocol.

## **Communication channel**

It is the endpoint of message delivery, the means used by the publisher or subscriber to communicate. It can be a social media tool, e-mail or SMS service or a distributed network.

## **Log**

It holds the track of message delivery with the encrypted content to help the maintenance and troubleshooting of the messaging services.

## **Routing Policy**

Routing policy is the essential, configurable service of the Messaging BB, published in the Information Mediator BB and is enabling the publishers and subscribers to pre-define and use the appropriate routing policy for the particular messaging event. In more advanced implementations, the Routing Policy can be applied for the Messaging Rooms (TBD).&#x20;
