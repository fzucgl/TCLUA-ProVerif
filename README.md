# TCLUA-ProVerif

This repository provides the official [ProVerif](https://proverif.inria.fr/) model of TCLUA (Trust-Coupled Lightweight User Authentication and Key Agreement) for industrial human-cyber-physical systems (HCPS) and the Industrial Internet of Things (IIoT).

It accompanies the manuscript:

> Guiliang Chen, Jie Huang, Jingli Huang, and Shangkun Liu, “TCLUA: Trust-Coupled Lightweight User Authentication and Key Agreement for Industrial Human-Cyber-Physical Systems,” IEEE Internet of Things Journal.

## File

- [`tclua.pv`](tclua.pv) — official applied-pi model used with ProVerif 2.05.

## How to run

Install [ProVerif 2.05](https://proverif.inria.fr/). From this directory:

```bash
proverif tclua.pv
```

On Windows, run the official binary, for example:

```bat
proverif.exe tclua.pv
```

A successful run of this model with ProVerif 2.05 reports `is true` for all six queries:

1. `not attacker(SKij)`
2. `not attacker(Kf)`
3. `inj-event(GWAcceptU(tid,Qu)) ==> inj-event(UBegin(tid,Qu))`
4. `inj-event(TAcceptTicket(sid,ver,n3)) ==> inj-event(GWIssue(sid,ver,n3))`
5. `inj-event(UAcceptT(sid,n5)) ==> inj-event(TRespond(sid,n5))`
6. `not attacker(SKij)` after leakage of `d_i`, `x`, and `y` (phase 1)
