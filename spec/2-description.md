# 2 Description

{% hint style="success" %}
Set the context of the Building Block for the reader. The description should not assume that the reader has any experience of the GovStack system other than that found on the GovStack website.
{% endhint %}

Utilizing a secure communication protocol, Messaging BB establishes a communication channel between GovStack services and end customers, citizens, in a GovStack implementation.

1. For **green-fields development**, it helps developers to build communication components on top of different GovStack services to make use of the federated architecture and passing messages, including machine and human triggered (both synchronous and asynchronous) messages .
2. Messaging BB is a standalone messaging gateway/client/proxy (including all possible modalities: email, SMS etc), but can also facilitate connections with **existing messaging service providers, hence** it is making **the adoption process less disruptive** for end users.

This BB can be used for messaging events in many different applications and use cases such as:

* Example A, encrypted: after being enrolled into a Health Care Program for the mothers of a newborn child, a woman/caretaker receives a message from the Health Care Service Provider about a doctors' appointment. The message is routed to an existing communication channel/application, in use and provided by the mother.
* Example B: unencrypted - a reminder/notification message from the service provider to the mother about the same appointment. If a doctor decides to hold the consultation remotely, a link is sent to the mother and a video consultation is started (conference is started and users join the room). The event is triggered by the Scheduler component and a new message is processed to the client.
* Example C: user-initiated message about a doctor consultation, targeted to a HCP phone number or a chatbot url (universal or targeted messaging back to the system).
