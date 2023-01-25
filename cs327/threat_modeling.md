# Threat Modeling

Data Flow Model Assets
* externel entities
  * people
  * systems
* process
  * threads
  * services
* data store
  * files
  * databases
  * registry
* data flow
* boundary
  * system boundaries
  * network boundaries
  * negative and positive boundary

STRIDE: Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Evelation of privilege

Spoofing: creating unauthorized copies of credentials (piracy)
Tampering: unauthorized modification or deletion of data items (transit or stored)
Repudiation: undermines authentication and transmission
(delivery denial, claiming things that are not ours)
Information disclosure: data leaks (even if transmission is authorized but ends up at wrong location)
Denial of service: targeting availability (prevent access to service)
Evelation of privilege: start out as standard user then gaining admin or higher level of privilege (can be done socially by getting someones password)

General STRIDE application guidlines for DFD
* Process: STRIDE
* Data flow: TID
* Data store: TID
* Data store(logs): TRID
* External entity: SR

identify threats -> create attack trees

we are now avoiding neutral zones, all areas in a DFD is either trusted or untrusted

## Example of threat tree
(1) Browser
Spoofing - requests to (2) (maybe phishing)
(2) Process, (3) Externel dll
Spoofed - create widget command (2)
more on slides

Circle/oval = Process (driving the component or application)
Rectangle = Externel entity (not sure if driven by executable)

## Threat analysis vs Threat modeling
Threat modeling: defensive approach
* designer/developer viewpoint
Threat analysis: offensive approach



## Notes for HA1
User is an externel entity
Remote webserver could be externel entity or process (rectangle)

Do not use software assisted modeling tools



