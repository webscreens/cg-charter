# Requirements for Presentation API protocols 

This document is a working draft that captures a set of technical requirements
for the network protocols to be developed by the Second Screen Community Group.

Below, the term "controller" is used as short for a controlling user agent and
"receiver" as short for a receiving user agent.  "Presentation Display" refers
to the network-connected device that hosts the receiving user agent.

## <a name="spec-ddc"></a>Presentation Display Discovery and Connection requirements

The following requirements apply to the proposed specification, <em>Presentation
Display Discovery and Connection</em>.

### <a name="REQ-D01"></a>REQ-D01: Presentation Display Discovery

The controller shall be able to discover the presence of a receiver connected to
the same IPv4 or IPv6 subnet.  It shall be able to obtain the IPv4 or IPv6
address of the receiver, a human readable name for the presentation display, and
an IP port number to initiate connectivity to the receiver.

### <a name="REQ-D02"></a>REQ-D02: Presentation Display Status

If the receiver so configured, the controller shall be able to determine if the
receiver has one or more active presentations.

If the receiver is so configured, the controller will also be able to discover
presentation URLs and presentation IDs of those presentations.

If a receiver is no longer available to a controller (or vice versa) (by losing
power, becoming disconnected from the network, etc.), the controller will be
able to determine this change within 30 seconds.

### <a name="REQ-D03"></a>REQ-D03: Presentation Connection Establishment

The controller must be able to intitiate and terminate a connection to the
receiver.

### <a name="REQ-D04"></a>REQ-D04: Presentation Connection Functions

* Connect and disconnect to/from multiple browsing contexts in each user agent
* Send messages to/from multiple browsing contexts

### <a name="REQ-D05"></a>REQ-D05: Presentation Connection Messaging Characteristics

* Reliability, in-order
* Desirable latency
* Message size

## <a name="spec-sec"></a>Presentation Display Security Requirements

* TLS 1.3
* Strong ciphers
* No weird legacy SSL/TLS features
* Bind channel to human visible name
* First-time verification & reverification on name/network change
* Controller trust store management
* Hardware TPM?

## <a name="spec-rendering"></a>Presentation Display Remote Rendering Requirements

TBD

## <a name="spec-playback"></a>Presentation Display Remote Playback Requirements

TBD

## References

