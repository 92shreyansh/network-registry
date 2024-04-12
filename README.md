# network-registry

some baseline assumption:
- NP vlookup needs to be signed by the NP and will be validated againts a unique key under the TTL.
- vlookup can only include elements of context & header in a p2p transaction which are transaction agnostic
- counterparty subcriber_id, ukId, domain(For Network_id/Domain), location
- considering 2 header values will result into unique in a Network Registry but this somewhere also centralises is a limitation


examples below
one illustration of the architecture where in the factors considered are the Registry would look out to the known parent not here we will try to evaluate the possibility by some comparison and certain underlying assumption of DNS registry enabled modal

In a DNS Server the search has few layers based on the address it is trying to identify like for www.ondc.org and here there are possible 3 recursion but in the case of the beckn protocol the recursion itself enables endless governance and inter registry by nature considering the availability of domain and location   

```mermaid
sequenceDiagram
    participant NP as Network Participant
    participant LR as Local Registry
    participant NR as Network Registry
    participant RR as Root Registry
    NP->>LR : /vlookup NP
    opt Details Not found Locally
        opt Network Unknown
            LR->>RR: /vlookup Network
            RR->>LR: /vlookup Network Response
        end
        LR->>NR: /vlookup NP
        NR->>LR: /vlookup NP Response
    end
    LR->>NP: /vlookup NP Response
```
