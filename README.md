# Meldepflichtige Laborbefunde

Neuerungen bei den Labormeldungen:

* Übermittlung der Statistiken ?
* Clostridium botulinum => Ausländische Labore

## Aussergewöhnlicher klinischer oder laboranalytischer Befund

Ungewöhnlicher oder unerwarteter Befund, der Massnahmen zum Schutz der öffentlichen Gesundheit erfordern könnte.

## Häufung von klinischen oder laboranalytischen Befunden

## Sentinella Labore (Kostenträger für Sentinella Erhebungen: BAG)

## HIV-Infektion

Positiver Befund: muss gemäss Vorgaben des HIV-Test-konzepts des BAG bestätigt werden, bevor die Meldung erfolgt.
Personendaten: 1. Buchstaben und Länge des Vornamens
*Statistik*: Gesamttotal der Tests eines Kalenderjahrs, davon die Anzahl reaktiver Tests (inklusive falsch reaktive), davon die Anzahl der bestätigt positiven Befunde (HIV-Meldelabors zählen nur die Bestätigungen von eigenen Screeningtests). Statistik über diagnostische Tests (ohne Blut-spende) aufführen.

## Influenzae, neuer Subtyp, saisonale Grippe

*Covid-19*
Diagnostizierende Laboratorien melden:

* die mittels molekularbiologischen Analysen (z.B. PCR) nachgewiesenen positiven individuellen Befunde innerhalb von 24 Stunden an das Kantonsarztamt und das BAG
* die mittels Schnelltest nachgewiesenen individuellen positiven Befunde innerhalb von 24 Stunden an das BAG
* die mittels molekularbiologischen Analysen (z.B. PCR) oder Schnelltest nachgewiesenen individuellen negativen Befunde innerhalb von 24 Stunden an das BAG
* die mittels molekularbiologischen Analysen (mutationsspezifische PCR oder Genomsequenzierung) nachgewiesenen Sars-CoV-2-Genomvarianten11 innerhalb von 24 Stunden an das BAG

## Meldeverordnung - Meldewege

[Gesetzgebung] <https://www.fedlex.admin.ch/eli/cc/2015/892/de>

Art. 12
Meldewege für laboranalytische Befunde und Befunde zu SarsCoV-2-Antigen-Schnelltests

1. Laboranalytische Befunde und Befunde zu Sars-CoV-2-Antigen-Schnelltests müssen dem BAG und gleichzeitig der Kantonsärztin oder dem Kantonsarzt des Kantons gemeldet werden, in dem die betroffene Person ihren Wohnsitz hat oder sich aufhält. Ist der Wohnsitz oder Aufenthaltsort der betroffenen Person unbekannt, so muss der Befund der Kantonsärztin oder dem Kantonsarzt des Kantons gemeldet werden, in dem die Beobachtung gemacht wurde.11
2. Laboranalytische Befunde aufgrund von Umweltproben müssen dem BAG und gleichzeitig der Kantonsärztin oder dem Kantonsarzt des Kantons gemeldet werden, in dem die Probe entnommen wurde.
3. Elektronische Meldungen laboranalytischer Befunde und von Befunden zu SarsCoV-2-Antigen-Schnelltests müssen ausschliesslich an das BAG gerichtet werden; dieses leitet sie unverzüglich an die Kantonsärztinnen und Kantonsärzte weiter.

## FHIR Format für Labormeldungen

Bundle
type document
versus
first entry resource: Composition
type message
first entry resource: MessageHeader

* event[x] => ValueSet observation-interpretation [http://terminology.hl7.org/CodeSystem/v3-ObservationInterpretation] ?Presence of Microorganism?
* destination
* sender, enterer, author
* source: name of systems, software (LIS?)
* Reason (CodeableConcept)
* Response, ID, code: ok|transient-error|fatal-error
* focus

## Messaging using FHIR Resources

[ <https://www.hl7.org/fhir/messaging.html>]
In FHIR messaging, a "request message" is sent from a source application to a destination application when an event (Trigger, Microorganism found) happens. Events mostly correspond to things that happen in the real world. The request message consists of a Bundle identified by the type "message", with the first resource in the bundle being a MessageHeader resource. The MessageHeader resource has a code - the message event - that identifies the nature of the request message, and it also carries additional request metadata. The other resources in the bundle depend on the type of the request, here probably observations.

The events supported in FHIR, along with the resources that are included in them, are defined below.

The destination application processes the request and returns one or more response messages which are also a bundle of resources identified by the type "message", with the first resource in each bundle being a MessageHeader resource with a response section that reports the outcome of processing the message and any additional response resources required.

Example Request Message
Example Response Message
