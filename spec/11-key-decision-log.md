# 11 Key Decision Log

{% hint style="info" %}
Record a list of key decisons made in the Building Block project so that new contributors can understand the context of the content.
{% endhint %}

A key decision log is to capture the evolution of decisions for future team members.

&#x20;

## **Meeting notes:**

Definition: Messaging BB is receiving messages from IM and relaying to the citizens. Essentially a black box, enabling to send messages to the end users.

* Key Functionality: Messaging BB should be able to be self-sustainable from the point of view of enabling to build e-mail client or SMS gw.
* Modalities: email, SMS, internet based apps like WhatsApp (botbased) social media apps, low footprint messages to devices.
* Specifications of JSON, REST etc,
* The minimum modalities-channels are built in, and it has to be scalable, comprehensive and priorizable. This can be part of a policy.
* Key Dependancy on IM and Workflow BB in order to deliver notifications of interactions. For example we need to define after 2-4 bounces of SMS-s that the transactions fail. At the end of the interaction, Workflow BB should take care of it.

#### &#x20;Need to be further defined:

CURRENT SCOPE.

Subscriber, push and pull are both in scope

#### FUTURE SCOPE.

Chat and message rooms for creating personal assistant for delivery of information and subscribing to gov services.

Government Application (Wallet etc).

#### OUT OF SCOPE.

Fully offline and no internet connection scenarios. Real time video- and audioconferencing.

### **Use cases to be mapped out and detailed in section:**

Registration of newborn child, message confirming the registration (partly mapped)

Payment transfer, message confirming the success of transfer

Booking appointment to a clinic, reminder about an appointment, scheduling an alert. Confirmation and reminder.

Emergency cenario vs normal cenario

&#x20;

NB! Sender will always have the address of the receiver to whom the information should be delivered to.

Receivers do not have the option to refuse.

Whatsapp has a policy in case mass messaging, the user should an option to opt out. Also there is a question of labeling the messages, to aviod spam. You have to mandate the SENDER ID to be factored in (source, type, ID).&#x20;

Machine level translation and handling different languages is outside the BB.

&#x20;

**14.01.2022 WG discussion and decisions.**

The use cases were reviewed, in particular the registration of the mother/child. Sending delivery confirmation of message and a queuing mechanism. By status we can give out information about this particular message (with a token). This is to keep track of the messages. In the queue we should also give an PRIORITY1 or PRIORITY2 to the messages. This applies not for emails, but sending SMS messages, an infrastructure and agreement should be set up to identify the type of message, carrying PRIORITY1 “label”, for creating the priority. Other types can be “PRIORITY2”.

Tasks: create workflow diagram for one of the the use cases and resource models. What data structures are required?

&#x20;

### **28.01.2022**

Rainer Türner gave an overview of the messaging BB capabilities, with the example of Payment request workflow.

Logging part got comments from Ramkumar to log the 1) Performance reasons 2) Administrative Requirements 3) Audit requirements.

We should give recommendations (for example NO SQL databases, postgre, denormalised dbss etc), what type of databases you should be using (ElasticSearch?). The most important thing of the databases is to use denormalised dbss.

Magnus got a confirmation to use what Matrix has, in order to populate the existing parts of the BB Messaging document.

Simon and Magnus presented the json schemas and best practices. Ramkumar asked if a logic can be built using the bot to retrieve the necessery information from another BB - as templates or any other standardized already existing information to increase productivity.

We agreed to look at the work that Ramkumar has done on his BB and to use his [Scheduler BB](https://drive.google.com/drive/folders/1IqIGUQZFBjnnrdwvAgibx2lXucX\_QHyE) as a model for building up the Messaging BB template.

&#x20;

### **11.02.2022**

John Cordeiro briefed on his additions to the Template.

Discussion was held on the division of labor, and a table was created, where the Matrix team was tasked with two chapters.

Agreed a meeting on Wednesday, 16.02.2022 with John and Rainer and Matrix guys to do joint writing of the following chapters: Data Structures and Service API-s.

GovStack Specs Work Mapping: [GovStack Specs Mapping](https://docs.google.com/spreadsheets/d/194sYMvzLXjIrJ5\_hveVoKJR5XjOHAHTX\_9Vnk9d3B\_E/edit?usp=sharing)

&#x20;

### **Meetings in March 2022**

The division of labour was detailed further, with John creating the generic Workflow Diagrams and Rainer detailing the forst version of the service API-s with the example of Matrix.

&#x20;

### **Meetings in April 2022**

31.03.2022 and 07.04.2022 at the inter-BB WG meetings, the first version of API descriptions and Workflow Diagrams were commented on by Max, Ramkumar and WG members. On April 11th, the initial BB Template was finalized by Martin and sent for internal review.



| 1.0.0                | Steve Conrad [sconrad@digitalimpactalliance.org](mailto:sconrad@digitalimpactalliance.org) | Initial version of the Template                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.1.0                | Max Carlson, Steve Conrad, Dr. Ramkumar, Trevor Kinsey from the Architecture Group         | Applied document standards to template                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 1.2.0                | Martin Karner, Rainer Türner (01.09.2021)                                                  | Drafted the first definition and started to assign the work on chapters to group members.                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 1.2.1                | BB WG members (29.10.2021)                                                                 | Drafted the Definition, decided to limit the scope of the BB to the messaging between the GovStack application/internal user and the end user (using i.e. Matrix protocol, routing to existing messaging modalities).                                                                                                                                                                                                                                                                                             |
| 1.2.3                | BB WG members (05.11.2021)                                                                 | Identified Messaging BB in the Logical Process Blueprint, and in particular the Registering use case. Drafted the [table of functional and technical requirements](https://docs.google.com/spreadsheets/d/19Ej86NKsBPY6hLF9Q-GNS4GSlICtTe7ABpOj2KTAqSA/edit?usp=sharing) for the registering use case.                                                                                                                                                                                                            |
| 1.2.4.               | BB WG members (12.11.2021)                                                                 | <p>Decisions made:</p><p>data storage and network transaction logs should be configurable;</p><p>performance should be monitored, metric installed;</p><p>Business logic and policy can be stored in separate BB and they can add MSG type, address: who-to-send-to, MSG channel etc.</p><p>In reverse communication, an unique identifier is created per user (upon registering at the Messaging BB or any other BB).</p><p>BB should allow push and pull models.</p><p>Need to sync with Taylor@IM/Workflow</p> |
| <p>1.2.5</p><p> </p> | Rainer Türner                                                                              | Initial set of cross-cutting requirements                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 1.2.7                | John Cordeiro and Martin Karner                                                            | Initial list of definitions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 1.2.8                | Magnus Hult, Martin Karner                                                                 | Miro table was drafted in order to map the high level functionalities, vis-a-vis the end users and other BB-s, workflows.                                                                                                                                                                                                                                                                                                                                                                                         |
| 1.2.9                | Rainer Türner                                                                              | Update of cross-cutting requirements                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| 1.3.0                | John Cordeiro                                                                              | Created a generic workflow diagram                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| 1.4.0                | Rainer Türner                                                                              | Created initial API descriptions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
