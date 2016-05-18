# Requirements for Presentation API protocols 

This document is a working draft that captures a set of technical requirements
for the network protocols to be developed by the [Second Screen Community
Group](https://webscreens.github.io/cg-charter/).  These requirements are
intended to guide the development of the specifications to be developed by the
Second Screen Community Group.

The terms *controlling user agent*, *receiving user agent*, *controlling
browsing context*, *receiving browsing context*, and *destination browsing
context* are defined in the [Presentation
API](https://w3c.github.io/presentation-api/).

Below, the term "controller" is used as short for a controlling user agent and
"receiver" as short for a receiving user agent.  "Presentation display" refers
to a network-connected device that hosts the receiving user agent.

## <a name="spec-ddc"></a>Presentation Display Discovery and Connection requirements

The following requirements apply to the proposed specification, *Presentation
Display Discovery and Connection*.

### <a name="REQ-D01"></a>REQ-D01: Presentation Display Availability

- A controller shall be able to discover the presence of a receiver connected to
the same IPv4 or IPv6 subnet and reachable by IP multicast.

- It shall be able to obtain the IPv4 or IPv6 address of the receiver, a human
readable name for the presentation display, and an IP address and port number of
the receiver.

*NOTE:* Requirements for presentation display discovery techniques other than
via the LAN, such as Bluetooth and NFC, will be embedded within the
corresponding non-normative reports.

### <a name="REQ-D02"></a>REQ-D02: Presentation Display Status

- If the receiver so configured, the controller shall be able to determine if the
receiver has one or more active presentations.

- If the receiver is so configured, the controller will also be able to discover
the presentation URLs and presentation IDs of those presentations.

- If a receiver is newly available to a controller (by connecting to the same
LAN, powering on, etc.) the controller shall be able to determine this status
change within a reasonable amount of time, so that pages using the
Presentation API can show receive presentation display availablity changes in
a timely manner.

- If a receiver is no longer available to a controller (or vice versa) (by
losing power, becoming disconnected from the network, etc.), the controller (or
receiver) will be able to determine this status change within a reasonable
amount of time, so that pages using the Presentation API can show receive
presentation display availablity changes in a timely manner.

### <a name="REQ-D02"></a>REQ-D03: Presentation URL Compatibility

- The controller shall be able to determine if the receiver is compatible with a
specific presentation URL.

### <a name="REQ-D04"></a>REQ-D04: Presentation Connection Establishment

- A controller shall be able to connect to a receiver given its IP address and port.

- A controller shall be able to terminate a connection with a receiver, and vice versa.

## <a name="spec-sec"></a>Presentation Display Security Requirements

The following requirements apply to the proposed specification, *Presentation
Display Security*.  These are high level requirements which will become more
specific as the security architecture evolves.

- Communication between the controller and receiver shall be confidential, to prevent
passive eavesdropping attacks.

- The controller shall be able to authenticate that the receiver is same device
that is shown to the user when permission is granted for starting a presentation,
to prevent man-in-the-middle attacks.

## <a name="spec-rendering"></a>Presentation Display Remote Rendering Requirements

The following requirements apply to the proposed specification, *Presentation
Display Remote Rendering*.

### <a name="REQ-R01"></a>REQ-R01: Creating A Receiving Browsing Context

- A controller shall be able to request the creation of a receiving browsing
context on an available receiver, given a Presentation ID and Presentation
URL.

- The receiver shall be able to return the outcome of the creation request to the
controller (success or failure).

### <a name="REQ-R02"></a>REQ-D02: Terminating A Receiving Browsing Context

- A controller shall be able to request the termination of a receiving browsing
context on a receiver, given a Presentation ID and Presentation URL.

- The receiver shall be able to return the outcome of the termination request to
the controller (success or failure).

### <a name="REQ-R03"></a>REQ-D03: Receiving Browsing Context Status Change

- A receiver shall be able to notify a connected controller when a receiving
browsing context has been terminated (other than via the termination request
above).

- The notification shall be sent no later than 5 seconds after the receiving
browsing context has been terminated.

### <a name="REQ-R04"></a>REQ-D04: Presentation Connections Between Browsing Contexts

- A controller shall be able to connect a specific controlling browsing context to a
specific receiving browing context in a receiver.

- A controller shall be able to disconnect a specific controlling browsing context to a
specific receiving browing context in a receiver.

- A receiver shall be able to disconnect a receiving browsing context from a
specific controlling browing context in a controller.

### <a name="REQ-R05"></a>REQ-D05: Presentation Connection Messaging

- A user agent shall have a way to address a message to a specific destination
browsing context.

- From a given browsing context, messages sent to the destination browsing
context shall arrive in-order.  This means: if message A is sent before
message B on a single PresentationConnection, then a `message` event on the
destination PresentationConnection with A will fire before a `message` event
with B.

- The latency to transmit a message from the controller to the receiver shall
approximate the network latency between the user agents (accounting for
message size and reasonable protocol overhead).

- The destination user agent shall have a way of preventing the sending user
agent from transmitting messages faster than they can be consumed.

- For DOMString, ArrayBuffer, and ArrayBufferView messages, controllers and
receivers shall support messages up to 4 megabytes in size.

- For Blob messages, controllers and receivers shall support messages up to 256
megabytes in size.

- DOMString messages shall be transmitted in UTF-8.

## <a name="spec-playback"></a>Presentation Display Remote Playback Requirements

TBD.

## References

TBD.

