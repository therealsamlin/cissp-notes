# CISSP Brain Dump Sheet
Write this down at the start of your exam.

---

## FORMULAS
```
ALE = SLE × ARO
SLE = AV × EF
(If control cost < ALE → worth it)
```

## INCIDENT RESPONSE (DRMRRRL)
```
Detect → Response → Mitigate → Report → Recovery → Remediation → Lessons Learned
```

## SDLC (RDITE)
```
Real Developers Ideas Take Effort
Requirements → Design → Implementation → Testing → Evolution (maintenance)
```

## SECURITY MODELS
```
Bell-LaPadula (Confidentiality): No read UP, no write DOWN | * = write
Biba (Integrity): No read DOWN, no write UP
Clark-Wilson: Access through programs only
Brewer-Nash: Chinese Wall
```

## CLASSIFICATION
```
Government: Top Secret > Secret > Confidential > Unclassified
Commercial: Confidential > Private > Sensitive > Public
```

## RAID
```
0 = Stripe (no fault tolerance)
1 = Mirror (1 disk)
5 = Stripe + Parity (1 disk)
6 = Double Parity (2 disks)
10 = Mirror + Stripe (best performance + redundancy)
```

## BACKUP
```
Full = everything, fastest restore
Incremental = since last backup, fastest backup, slowest restore
Differential = since last full, middle ground
```

## RECOVERY SITES
```
Hot = ready (minutes) | Warm = partial (hours) | Cold = empty (days)
```

## OSI LAYERS (7→1)
```
Please Do Not Throw Sausage Pizza Away
Application, Presentation, Session, Transport, Network, Data Link, Physical
```

## KEY PORTS
```
21=FTP | 22=SSH | 23=Telnet | 25=SMTP | 53=DNS
80=HTTP | 443=HTTPS | 389=LDAP | 636=LDAPS | 3389=RDP
```

## TESTING
```
SAST = Static = Source code (white-box)
DAST = Dynamic = Running app (black-box)
```

## WIRELESS
```
WEP = broken (RC4, 24-bit IV)
WPA = weak (TKIP)
WPA2 = good (AES-CCMP)
WPA3 = best (SAE)
```

## ACCESS CONTROL
```
MAC = system enforces (labels) — Bell-LaPadula, Biba
DAC = owner decides
RBAC = roles/groups
ABAC = attributes (time, location, etc.)
```

## IPsec
```
AH = integrity + auth only (no encryption, breaks NAT)
ESP = encryption + integrity + auth (use this)
Transport = host-to-host | Tunnel = gateway-to-gateway
```

## CMMI
```
1=Initial(chaos) | 2=Managed(project) | 3=Defined(org) | 4=Quantitative | 5=Optimizing
```

## DR METRICS
```
RTO = time to restore | RPO = acceptable data loss | MTD = max downtime
MTD = RTO + WRT
```

## DATABASE RECOVERY
```
Shadowing = real-time (fastest, zero loss)
Journaling = logs (fast, minimal loss)
Vaulting = batch (slower, some loss)
Full backup = slowest
```

## MISC
```
Kerberos = symmetric, uses tickets, port 88
RADIUS = UDP, end users, encrypts password only
TACACS+ = TCP, admins, encrypts entire packet

False positive = false alarm
False negative = missed detection (worse)

Due diligence = research/plan
Due care = implement/do
```
