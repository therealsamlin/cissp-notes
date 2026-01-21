# CISSP Memorization Guide

---

## Risk Management

### Security Planning Horizons

| Plan Type | Timeframe | Focus | Example |
|-----------|-----------|-------|---------|
| **Strategic** | ~5 years | Long-term vision, goals | Security program roadmap, major investments |
| **Tactical** | ~1 year | Mid-term projects | Annual training plan, tool deployments |
| **Operational** | Monthly/Quarterly | Day-to-day tasks | Patch schedules, log reviews, audits |

---

### Risk Response Types

| Risk Response | What It Means | Example |
|---------------|---------------|---------|
| **Assignment/Transfer** | Give risk to someone else | Insurance, outsourcing |
| **Mitigation** | Reduce impact or likelihood | Patches, training |
| **Avoidance** | Eliminate the risk entirely | Cancel project |
| **Acceptance** | Acknowledge and live with it | No action taken |

**Exam Trap:** Insurance = Assignment (NOT Acceptance)

---

### Quantitative Risk Analysis

| Term | Formula | Meaning |
|------|---------|---------|
| **AV** | — | Asset Value |
| **EF** | — | Exposure Factor (% of asset lost) |
| **SLE** | AV × EF | Single Loss Expectancy |
| **ARO** | — | Annual Rate of Occurrence |
| **ALE** | SLE × ARO | Annual Loss Expectancy |

**Example:**
- Server worth $100,000 (AV)
- Fire destroys 50% of it (EF = 0.5)
- SLE = $100,000 × 0.5 = $50,000
- Fire happens once every 10 years (ARO = 0.1)
- ALE = $50,000 × 0.1 = $5,000/year

**Exam use cases:**
- "Should we spend $10,000/year on control?" → Compare to ALE
- Control cost < ALE → Worth it
- Control cost > ALE → Not worth it

---

### Power Issues

| Issue | Duration | Description |
|-------|----------|-------------|
| **Sag** | Momentary (seconds) | Brief voltage drop |
| **Brownout** | Extended (hours) | Prolonged low voltage |
| **Spike** | Momentary | Quick voltage surge |
| **Blackout** | Extended | Complete power loss |

---

## Physical Security

### Fire Classes

| Class | Fire Type | Suppression | Memory Aid |
|-------|-----------|-------------|------------|
| **A** | Ordinary (wood, paper) | Water | A = Ash |
| **B** | Liquids (gas, oil) | Halon, CO2 | B = Barrel |
| **C** | Electrical | Halon, CO2 | C = Current |
| **D** | Metals | Dry powder | D = Dynamite metals |
| **K** | Kitchen (oils, grease) | Wet chemical/Alkaline | K = Kitchen |

**Key Rules:**
- Water = Class A only (never electrical)
- Dry powder = Class D only (metals)
- Halon/CO2 = B and C

---

### Sprinkler Systems

| Type | Pipe Contents | Head Closed? | Activation | Use Case |
|------|---------------|--------------|------------|----------|
| **Wet Pipe** | Water | Yes | Heat melts head | Most common, fastest |
| **Dry Pipe** | Compressed air | Yes | Heat opens head → water flows | Cold environments |
| **Preaction** | Air (until triggered) | Yes | Two-stage: 1) Detection fills pipe, 2) Heat opens head | Data centers, museums |
| **Deluge** | Air | **No** | Detection opens valve → ALL heads release | High-hazard areas |

**Exam Traps:**
- Protects against accidental discharge → **Preaction**
- Best for data center → **Preaction**
- Cold warehouse → **Dry Pipe**
- Fastest response → **Wet Pipe**
- Uses most water → **Deluge**

---

## Security Models

### Bell-LaPadula vs Biba

| Model | Focus | Star (*) Property | Explanation |
|-------|-------|-------------------|-------------|
| **Bell-LaPadula** | Confidentiality | No Write DOWN | Prevents leaking secrets to lower levels |
| **Biba** | Integrity | No Write UP | Prevents corrupting higher integrity levels |

### Security Models Summary

| Model | Focus | Industry | Access Control | Key Concept |
|-------|-------|----------|----------------|-------------|
| **Bell-LaPadula** | Confidentiality | Military | MAC (labels) | No read up, no write down |
| **Biba** | Integrity | Military/Commercial | MAC (labels) | No read down, no write up |
| **Clark-Wilson** | Integrity | Commercial | MAC (programs) | Access via authorized programs only |
| **Brewer-Nash** | Conflict of Interest | Finance/Legal | MAC (dynamic) | Chinese Wall — blocks based on access history |

**Clark-Wilson:** Users access data only through authorized programs (TPs). Example: Bank teller uses banking app, cannot run direct SQL.

**Brewer-Nash:** Once you access one competitor's data, you're blocked from accessing others. Prevents conflicts of interest.

---

### Control Categories

| Category | What It Is | Examples |
|----------|------------|----------|
| **Administrative** | Policies, procedures, people | NDAs, contracts, security policies, background checks, training |
| **Technical (Logical)** | Hardware/software controls | Firewalls, encryption, access control, IDS, antivirus |
| **Physical** | Protect physical environment | Mantraps, fences, guards, locks, CCTV, bollards |

---

### Control Types (Functions)

| Type | Function | Examples |
|------|----------|----------|
| **Directive** | Instructs/mandates behavior | Policies, standards, procedures, training |
| **Preventive** | Blocks threats | Firewall, locks, encryption |
| **Detective** | Discovers incidents | Logs, IDS, cameras, alarms |
| **Corrective** | Fixes after incident | Patches, restore, reboot |
| **Deterrent** | Discourages attacks | Warning signs, guards |
| **Compensating** | Alternative control | Manual review when automation fails |

**Key Distinctions:**
- Directive = tells you what to do (policy)
- Preventive = forces/blocks (technical enforcement)
- Deterrent = discourages but doesn't block

---

## Threat Frameworks

### STRIDE vs DREAD

| Framework | Purpose |
|-----------|---------|
| **STRIDE** | Categorizes threat types |
| **DREAD** | Rates threat severity |

**STRIDE (Threat Categories):**
- **S**poofing (fake identity)
- **T**ampering (modify data)
- **R**epudiation (deny actions)
- **I**nformation Disclosure (data leak)
- **D**enial of Service
- **E**levation of Privilege

**DREAD (Severity Rating):**
- **D**amage potential
- **R**eproducibility
- **E**xploitability
- **A**ffected users
- **D**iscoverability

---

## Cryptography

### Crypto Quick Reference

| Purpose | Algorithm |
|---------|-----------|
| Key exchange | DH, ECDHE |
| Bulk encryption | AES |
| Digital signatures | DSA, RSA |
| Hashing | SHA, MD5 |

**Forward Secrecy** = DH/ECDHE (ephemeral keys protect past sessions)

---

### Block vs Stream Ciphers

| Type | Method | Examples |
|------|--------|----------|
| **Block** | Fixed chunks | AES, DES, RC5, Blowfish |
| **Stream** | Bit by bit | RC4 |

---

### Block Cipher Modes

| Mode | Full Name | IV? | XOR? | Type | Error Propagation | Exam Keyword |
|------|-----------|-----|------|------|-------------------|--------------|
| **ECB** | Electronic Codebook | No | No | Block | N/A (patterns visible) | Weakest, never use |
| **CBC** | Cipher Block Chaining | Yes | Yes | Block | Yes | Most common |
| **OFB** | Output Feedback | Yes | Yes | Stream | No (errors stay **O**ut) | No error propagation |
| **CFB** | Cipher Feedback | Yes | Yes | Stream | Yes (errors **C**hain) | Stream cipher |
| **CTR** | Counter | No (uses counter) | Yes | Stream-like | No | Parallel, fast |
| **GCM** | Galois/Counter Mode | Yes | Yes | Stream-like | No | Encryption + authentication |

**Exam Traps:**
- Patterns visible → ECB
- Acts as stream cipher → CFB, OFB (both have "Feedback")
- No error propagation → OFB, CTR
- Parallel encryption → CTR
- Encryption + authentication → GCM

---

### Digital Signatures

**How it works:**

1. Sender hashes the message
2. Sender encrypts hash with their **private key** → signature
3. Receiver decrypts signature with sender's **public key**
4. Receiver hashes the message and compares

**Provides:**
- **Authentication** — proves sender identity
- **Integrity** — detects tampering
- **Non-repudiation** — sender can't deny sending

**Does NOT provide:** Confidentiality (message isn't encrypted)

---

### Symmetric vs Asymmetric

| Type | Key Usage | Examples |
|------|-----------|----------|
| **Symmetric** | Shared secret | AES, DES, Kerberos |
| **Asymmetric** | Key pairs | RSA, ECC, DSA, DH |

**Exam Trap:** Kerberos uses symmetric keys

---

### Kerberos Authentication

| Term | Full Name | Role |
|------|-----------|------|
| **KDC** | Key Distribution Center | Central auth server (AS + TGS) |
| **AS** | Authentication Server | Issues TGT |
| **TGS** | Ticket Granting Service | Issues Service Tickets |
| **TGT** | Ticket Granting Ticket | Ticket to get other tickets |

**Flow:**
```
User → AS → TGT
User + TGT → TGS → Service Ticket
User + Service Ticket → Service → Access
```

**Key Points:**
- KDC = AS + TGS (same server)
- Uses symmetric keys (pre-shared)
- Timestamps prevent replay attacks

---

### Common Criteria (CC) & EAL Levels

**Common Criteria** = ISO 15408, international standard for security product evaluation.

| Term | Full Name | Description |
|------|-----------|-------------|
| **TOE** | Target of Evaluation | Product being tested |
| **PP** | Protection Profile | Requirements for product category |
| **ST** | Security Target | Vendor's specific claims |

**EAL Levels:**

| Level | Description |
|-------|-------------|
| EAL 1-3 | Basic to methodical testing |
| **EAL 4** | Commercial ceiling |
| EAL 5-6 | Semiformally verified (government) |
| **EAL 7** | Highest — formally verified |

**Example (Healthcare App):**
```
1. Identify TOE:        Prescription management app
2. Find applicable PP:  Healthcare / Medical Device PP
3. Write ST:            "Our app meets PP requirements + extra features"
4. Lab evaluates:       Independent lab tests claims against TOE
5. If verified:         Receive EAL4 certification
```

**Exam Traps:**
- EAL9+ does not exist
- Highest commercial = EAL4
- Independent lab performs evaluation, not vendor

---

### TPM vs HSM

| Device | Location | Purpose |
|--------|----------|---------|
| **TPM** | On motherboard | Stores keys, boot integrity |
| **HSM** | External device | High-security crypto operations |

---

### PUF vs RoT

| Concept | Purpose | Example |
|---------|---------|---------|
| **PUF** (Physical Unclonable Function) | Unique hardware identity | SRAM PUF, Ring Oscillator PUF |
| **RoT** (Root of Trust) | Foundation of trust chain | TPM, Secure Boot ROM, HSM |

---

## Identity and Access Management

### Trusted Computing Base (TCB)

| Term | Description |
|------|-------------|
| **TCB** | All hardware/firmware/software that enforces security policy |
| **Security Perimeter** | Boundary between TCB and untrusted components |
| **Reference Monitor** | Concept — abstract machine that mediates all access |
| **Security Kernel** | Implementation of reference monitor |

**Reference Monitor properties:**
- Always invoked (can't be bypassed)
- Tamper-proof
- Small enough to verify

**Key point:** Smaller TCB = more secure (less attack surface)

---

### System Security Modes

| Mode | Clearance | Need-to-Know | Description |
|------|-----------|--------------|-------------|
| **Dedicated** | All users cleared for ALL data | All users approved for ALL data | Everyone cleared for everything |
| **System High** | All users cleared for highest level | NOT all approved for all data | Need-to-know varies |
| **Compartmented** | All users cleared for highest level | Formal approval per compartment | Compartmentalized access |
| **Multilevel** | Users have different clearances | Different need-to-know | System enforces MAC labels |

**Key points:**
- Dedicated = most restrictive (everyone must be cleared for everything)
- Multilevel = least restrictive, most trust in system (MAC enforcement)

---

### Data Classification

**Military/Government:**

| Level | Description |
|-------|-------------|
| **Top Secret** | Exceptionally grave damage to national security |
| **Secret** | Serious damage to national security |
| **Confidential** | Damage to national security |
| **Unclassified** | No damage if disclosed |

**Business/Commercial:**

| Level | Description |
|-------|-------------|
| **Confidential** | Most sensitive (trade secrets, financials) |
| **Sensitive** | Internal use, limited disclosure |
| **Private** | Personal data (PII) |
| **Public** | Open to everyone |

---

### Data Roles

**Internal Roles:**

| Role | Who | Responsibility |
|------|-----|----------------|
| **Data Owner** | Senior executive | Accountable, sets classification |
| **Data Custodian** | IT staff | Implements controls, backups |
| **Data User** | Employees | Uses data appropriately |

**GDPR Roles:**

| Role | Who | Responsibility |
|------|-----|----------------|
| **Data Controller** | Your organization | Decides why/how to process data |
| **Data Processor** | Third-party vendor | Processes data on behalf of controller |

---

### RADIUS vs TACACS+

| Protocol | Who Uses It | Transport | Description |
|----------|-------------|-----------|-------------|
| **RADIUS** | End users | UDP | Centralized auth for network access (WiFi, VPN). Auth+Authz combined. Encrypts password only. |
| **TACACS+** | Network admins | TCP | Centralized auth for device management (routers, switches). Auth/Authz/Accounting separate. Encrypts entire packet. |

**Usage examples:**
- RADIUS → Hotel guest WiFi, university eduroam, corporate WiFi, VPN login
- TACACS+ → Admin SSH to routers/switches/firewalls (same hotel could use both — RADIUS for guests, TACACS+ for IT staff)

---

### Access Control Models

| Model | Who Decides | Based On | Example |
|-------|-------------|----------|---------|
| **MAC** | System (enforced) | Labels | Military classifications |
| **DAC** | Owner | Owner's choice | Windows file sharing |
| **RBAC** | Admin | Role/Group | Permissions by job title |
| **ABAC** | Policy engine | Multiple attributes | Time + location + department |
| **Rule-Based** | System | IF/THEN rules | Firewall rules |

**Exam Questions:**
- System enforces, user can't change → MAC
- Owner controls access → DAC
- Permissions by job title → RBAC
- Multiple conditions evaluated → ABAC

---

## Operations Security

### Change Management Order

```
Request → Review → Approve → Test → Implement → Document
```

**Key:** Test BEFORE Implement

---

### Disaster Recovery Metrics

| Metric | Full Name | Meaning |
|--------|-----------|---------|
| **RTO** | Recovery Time Objective | Time to restore systems |
| **RPO** | Recovery Point Objective | Acceptable data loss |
| **MTD** | Maximum Tolerable Downtime | Business survival limit |
| **WRT** | Work Recovery Time | Time to verify after restore |

**Formula:** MTD = RTO + WRT

**Timeline:**
```
DISASTER ──→ RESTORE ──→ VERIFY ──→ NORMAL
   │←── RTO ──→│←─ WRT ─→│
   │←─────────── MTD ────────────→│
```

**Example:**
| Metric | Value | Type |
|--------|-------|------|
| RTO | 6 hours | Goal (what you aim for) |
| MTTR | 4 hours | Reality (what it takes) |
| WRT | 1 hour | Verify time |
| MTD | 8 hours | Limit (business dies after this) |

MTTR (4) + WRT (1) = 5 hours < MTD (8 hours) ✓ Safe

**Hardware Metrics:**

| Metric | Full Name | Meaning |
|--------|-----------|---------|
| **MTTF** | Mean Time To Failure | Time before failure (non-repairable) |
| **MTTR** | Mean Time To Repair | Time to fix |
| **MTBF** | Mean Time Between Failures | Time between failures (repairable) |

---

### Database Recovery Methods

| Method | What It Is | Recovery Speed | Data Loss |
|--------|------------|----------------|-----------|
| **Database Shadowing** | Real-time exact replica, always in sync | Fastest (immediate failover) | None (zero RPO) |
| **Remote Journaling** | Transaction logs sent to remote site, replay to restore | Fast (replay logs) | Minimal (last few transactions) |
| **Electronic Vaulting** | Batch transfer at intervals (hourly/daily) | Slower (restore batch + apply) | Some (depends on interval) |
| **Full Backup** | Complete offsite copy, periodic | Slowest (restore entire backup) | Most (since last backup) |

**Memory Aids:**
- **Shadowing** = Shadow follows you in real-time
- **Journaling** = Journal entries (logs) shipped off
- **Vaulting** = Vault jump with big heavy batch
- **Full Backup** = Old school tape truck

**Exam keywords:**
- Zero data loss → Shadowing
- Replay transactions → Remote Journaling
- Batch transfer → Electronic Vaulting
- RPO gets worse as you go down the table

---

### Recovery Sites

| Site | Equipment | Data | Recovery Time | Cost | Use Case |
|------|-----------|------|---------------|------|----------|
| **Hot** | Yes | Yes (real-time) | Minutes to hours | Highest | Banks, hospitals, stock exchange |
| **Warm** | Partial | Backups (not current) | Hours to days | Medium | Most businesses |
| **Cold** | No | No | Days to weeks | Lowest | Non-critical, budget-limited |
| **Mobile** | Portable | Varies | Varies | Flexible | Disaster zones, temporary needs |
| **Cloud** | On-demand | Backups | Hours | Pay-per-use | Startups, variable workloads |

**Exam use cases:**
- "Bank needs zero downtime" → Hot site
- "Limited budget, can tolerate 1 week recovery" → Cold site
- "Need flexibility, pay only when used" → Cloud site

---

### BCP Phases

**Phase 1: Development**
1. Policy
2. BIA (Business Impact Analysis)
3. Preventive Controls
4. Recovery Strategies
5. DRP (Disaster Recovery Plan)

**Phase 2: Testing**

| Test Type | Disruption |
|-----------|------------|
| Tabletop | None |
| Simulation | Minimal |
| Parallel | Low |
| Full-Interruption | High |

**Phase 3: Maintenance**
- Annual review
- Update after major changes

---

### RAID Levels

| RAID | Method | Fault Tolerance | Use Case |
|------|--------|-----------------|----------|
| **0** | Striping | None | Video editing, temp data (speed, no redundancy) |
| **1** | Mirroring | 1 disk | OS drive, boot drive (simple redundancy) |
| **5** | Striping + parity | 1 disk | File servers, general storage (balanced) |
| **6** | Double parity | 2 disks | Critical data, large arrays (high availability) |
| **10** | Mirror + stripe | 1 per mirror | Databases, high-performance apps (speed + redundancy) |

**Exam use cases:**
- "Maximum performance, no redundancy needed" → RAID 0
- "Database server needs speed AND redundancy" → RAID 10
- "Budget file server, can lose 1 disk" → RAID 5
- "Critical data, must survive 2 disk failures" → RAID 6

---

### Backup Types

| Type | What It Backs Up | Restore Needs | Use Case |
|------|------------------|---------------|----------|
| **Full** | Everything | Full only | Weekly backup, compliance archives |
| **Incremental** | Since last backup (any) | Full + all incrementals | Daily backups, limited storage |
| **Differential** | Since last full | Full + last differential | Balance of speed and restore time |

**Exam use cases:**
- "Fastest daily backup, limited storage" → Incremental
- "Fastest restore time" → Full
- "Balance backup speed and restore time" → Differential
- "Wednesday crash, need to restore" → Think about how many tapes needed

---

## Network Security

### Firewall Types

| Type | Layer | How It Works | Use Case |
|------|-------|--------------|----------|
| **Static Packet Filter** | 3-4 | Checks IP/port only, no state | Basic ACLs, routers |
| **Stateful (Dynamic)** | 3-4 | Tracks connection state | Standard enterprise firewall |
| **Circuit-Level Gateway** | 5 (Session) | Monitors TCP handshake, validates sessions | SOCKS proxy |
| **Application-Level Gateway** | 7 | Inspects content, breaks connection | High-security, web proxy |
| **NGFW** | 3-7 | Deep inspection + IPS + app awareness | Modern enterprise |

**Exam use cases:**
- "Block based on IP/port only, no context" → Static Packet Filter
- "Ensure reply packets match requests" → Stateful
- "Validates TCP handshake only" → Circuit-Level (Layer 5)
- "Inspect HTTP content for malware" → Application-Level or NGFW
- "Identify and block specific applications" → NGFW

**Key distinction:**
- Circuit-level = checks session is valid (TCP handshake), doesn't inspect content
- Application-level = inspects actual content/payload

---

### IDS/IPS Detection Methods

| Method | How It Works | Use Case |
|--------|--------------|----------|
| **Signature-based** | Matches known patterns | Known threats, low false positives needed |
| **Anomaly-based** | Compares to baseline | Zero-day detection, insider threats |
| **Heuristic** | Rules + behavior | Balance of both |

| Type | Action | Use Case |
|------|--------|----------|
| **IDS** | Alerts only (detective) | Monitoring, compliance, low-risk tolerance for blocking |
| **IPS** | Blocks traffic (preventive) | Active protection, inline deployment |

**Exam use cases:**
- "Detect unknown/new attacks" → Anomaly-based
- "Minimize false positives" → Signature-based
- "Must actively block, not just alert" → IPS
- "Network vs host monitoring" → NIDS vs HIDS

---

### Common Ports

| Port | Protocol | Service |
|------|----------|---------|
| 20/21 | TCP | FTP (data/control) |
| 22 | TCP | SSH, SCP, SFTP |
| 23 | TCP | Telnet (insecure) |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 67/68 | UDP | DHCP |
| 80 | TCP | HTTP |
| 88 | TCP/UDP | Kerberos |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 443 | TCP | HTTPS |
| 389 | TCP | LDAP |
| 636 | TCP | LDAPS |
| 1433 | TCP | MS SQL |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |

**Exam traps:**
- FTP = 21 (control), 20 (data)
- DNS = both TCP and UDP
- Secure version adds S or uses different port (LDAP 389 → LDAPS 636)

---

### TCP vs UDP

| Aspect | TCP | UDP |
|--------|-----|-----|
| Connection | Connection-oriented (3-way handshake) | Connectionless |
| Reliability | Guaranteed delivery, ordering | No guarantee |
| Speed | Slower | Faster |
| Use case | HTTP, FTP, SSH, email | DNS, DHCP, streaming, VoIP |

**TCP 3-way handshake:**
```
Client → SYN → Server
Client ← SYN-ACK ← Server
Client → ACK → Server
(Connection established)
```

**Exam use cases:**
- "Needs reliability" → TCP
- "Real-time, speed critical" → UDP
- "Which protocol for DNS?" → Both (UDP for queries, TCP for zone transfers)

---

### Wireless Security

| Standard | Encryption | Security |
|----------|------------|----------|
| **WEP** | RC4 (24-bit IV) | Broken — never use |
| **WPA** | TKIP (RC4) | Weak — deprecated |
| **WPA2** | AES-CCMP | Good — current standard |
| **WPA3** | AES-GCMP, SAE | Best — latest |

**Exam keywords:**
- WEP IV is too short (24-bit) → easily cracked
- WPA2 = AES = current standard
- WPA3 SAE = Simultaneous Authentication of Equals (protects against offline dictionary attacks)
- CCMP = Counter Mode with CBC-MAC Protocol

---

### 802.1X (Port-Based Authentication)

```
[Supplicant] ←→ [Authenticator] ←→ [Auth Server]
  (client)        (switch/AP)       (RADIUS)

1. Client connects to port
2. Port blocked until authenticated
3. Client sends credentials via EAP
4. Authenticator forwards to RADIUS
5. RADIUS approves → port opens
```

| Component | Role |
|-----------|------|
| **Supplicant** | Client device requesting access |
| **Authenticator** | Switch or wireless AP |
| **Authentication Server** | RADIUS server |

**Exam tip:** 802.1X = NAC at port level, uses EAP and RADIUS

---

### VPN Protocols

| Protocol | Encryption |
|----------|------------|
| OpenVPN | TLS/SSL |
| L2TP | None (pairs with IPsec) |
| PPTP | MPPE (deprecated) |
| IPsec | ESP/AH |
| WireGuard | ChaCha20 |

---

### RPC vs REST API

| Protocol | Layer | Description |
|----------|-------|-------------|
| **RPC** | Session (Layer 5) | Call function on remote server |
| **REST API** | Application (Layer 7) | Request a resource |

---

### Email Security

| Protocol | Function | Provides | Implementation |
|----------|----------|----------|----------------|
| **SPF** | Lists authorized sending servers | Authentication | DNS TXT record |
| **DKIM** | Cryptographic signature | Integrity + Authentication | Private key signs, public key in DNS |
| **DMARC** | Policy for SPF/DKIM failures | Policy enforcement | DNS TXT record (none/quarantine/reject) |

**Note:** None provide confidentiality — use S/MIME, PGP, or TLS for encryption.

**Flow:**

```
Email arrives from IP 203.0.113.5 claiming to be from @example.com
     ↓
1. SPF Check: Is 203.0.113.5 authorized to send for example.com?
   → Query: example.com TXT record
     ↓
2. DKIM Check: Is signature valid?
   → Query: selector._domainkey.example.com TXT record
     ↓
3. DMARC Check: What to do if SPF/DKIM failed?
   → Query: _dmarc.example.com TXT record
     ↓
Apply DMARC policy: none/quarantine/reject
```

**DNS Record Examples:**

```
SPF (which IPs can send):
example.com TXT "v=spf1 ip4:192.0.2.0/24 include:_spf.google.com -all"

DKIM (public key for signature verification):
selector._domainkey.example.com TXT "v=DKIM1; k=rsa; p=MIGfMA0GCS..."

DMARC (policy for failures):
_dmarc.example.com TXT "v=DMARC1; p=reject; rua=mailto:reports@example.com"
```

| DMARC Policy | Action |
|--------------|--------|
| `p=none` | Monitor only, no action |
| `p=quarantine` | Send to spam folder |
| `p=reject` | Block email entirely |

---

### DMZ (Demilitarized Zone)

Network segment between internet and internal network. Hosts public-facing services (web servers, reverse proxies) that need external exposure. If breached, attacker is contained — cannot directly access internal network.

```
Internet ←→ [Firewall] ←→ DMZ ←→ [Firewall] ←→ Internal Network
```

---

### VPN Tunnel Types

| Type | Traffic Through VPN | Security | Use Case |
|------|---------------------|----------|----------|
| **Full Tunnel** | All traffic | Higher | Regulated industries |
| **Split Tunnel** | Only company traffic | Lower | General remote work |

**Split Tunnel Example:**

| Destination | Route | Through VPN? |
|-------------|-------|--------------|
| `internal.company.com` | VPN | Yes |
| `10.0.0.x` (internal IP) | VPN | Yes |
| `google.com` | Direct to internet | No |
| `youtube.com` | Direct to internet | No |

**Trade-off:** Split tunnel risks home network compromise pivoting to company network.

---

### VLAN Hopping Attacks

**VLAN** = Logical network segmentation. Switch enforces isolation at Layer 2.

| Attack | How It Works | Exploits |
|--------|--------------|----------|
| **Double Tagging** | Frame with 2 VLAN tags; first switch strips outer tag, second switch forwards inner tag to target VLAN | Native VLAN (untagged traffic) |
| **Switch Spoofing** | Attacker negotiates trunk link with switch using DTP | Dynamic Trunking Protocol enabled |

**Why VoIP increases risk:** Port carries both voice + data VLANs → trunk-like behavior → more attack surface

**Double Tagging Attack Process:**

```
Normal frame:
┌──────────┬─────────┬─────────┬─────────┐
│ Dest MAC │ Src MAC │ Type    │ Payload │
└──────────┴─────────┴─────────┴─────────┘

Double-tagged frame (attacker crafted):
┌──────────┬─────────┬─────────────┬─────────────┬─────────┬─────────┐
│ Dest MAC │ Src MAC │ Outer Tag   │ Inner Tag   │ Type    │ Payload │
│          │         │ VLAN 1      │ VLAN 30     │         │         │
│          │         │ (native)    │ (target)    │         │         │
└──────────┴─────────┴─────────────┴─────────────┴─────────┴─────────┘

Step 1: Attacker sends double-tagged frame (Outer=Native VLAN, Inner=Target VLAN)
Step 2: Switch A strips outer tag (native VLAN behavior)
Step 3: Frame still has inner tag (VLAN 30)
Step 4: Switch B sees VLAN 30 tag → forwards to target VLAN
Step 5: Attacker's traffic reaches protected VLAN
```

**Mitigations:**
- Disable DTP (`switchport nonegotiate`)
- Change native VLAN from default (VLAN 1)
- Explicitly tag native VLAN traffic
- Set ports to access mode, not trunk

**Exam keywords:** VLAN hopping, double tagging, switch spoofing, DTP, native VLAN, 802.1Q, trunk port

---

### CSA (Cloud Security Alliance) Data Lifecycle

| Phase | What Happens | Security Focus |
|-------|--------------|----------------|
| **Create** | Data generated/collected | Classification, labeling, ownership assigned |
| **Store** | Data saved to storage | Encryption at rest, access controls, backup |
| **Use** | Data actively processed | Decrypted in memory, access controls, DLP |
| **Share** | Data transferred/distributed | Encryption in transit, DRM, access controls |
| **Archive** | Long-term retention | Encryption, integrity checks, compliance retention |
| **Destroy** | Permanent removal | Crypto-shredding, degaussing, physical destruction |

**Exam tips:**
- Classification happens at **Create** (before storage)
- **Use** is most vulnerable — data is decrypted
- **Archive** ≠ Backup — archive is compliance-driven
- **Destroy** method must match data sensitivity

---

### Data Protection Techniques

| Technique | What It Does | Example | Exam Keyword |
|-----------|--------------|---------|--------------|
| **Tokenization** | Replace with random token, vault stores mapping | `4111-1111-1111-1234` → `4111-1111-1111-9827` | PCI-DSS, credit cards, format-preserving |
| **Data Masking** | Hide portion of data | `123-45-6789` → `XXX-XX-6789` | Display to users, call centers |
| **Anonymization** | Remove identifiers permanently | Remove name, aggregate ages | GDPR, no longer PII, irreversible |
| **Pseudonymization** | Replace identifier with alias | `John Smith` → `EMP-0042` | GDPR, reversible with key |
| **Encryption** | Transform to unreadable ciphertext | `password` → `a1b2c3d4e5f6...` | Data at rest, in transit |
| **Hashing** | One-way transformation | `password` → `5f4dcc3b...` | Password storage, integrity |
| **Salting** | Add random value before hashing | `password` + `x7k2` → hash | Prevent rainbow tables |
| **Data Minimization** | Collect only what's needed | Don't store SSN if not required | GDPR, privacy by design |

---

### Data Remanence (Sanitization)

**Weakest to Strongest:**

| Method | Remanence | Description |
|--------|-----------|-------------|
| **Erasing** | Most | Deletes file pointer only (data still exists) |
| **Clearing** | Some | Overwrites with zeros/patterns |
| **Purging** | Minimal | Multiple overwrites, crypto-erase |
| **Degaussing** | Minimal | Magnetic field destroys data (HDDs/tapes only, not SSDs) |
| **Destruction** | None | Physical destruction (shredding, incineration) |

---

## Software Security

### Security Testing vs Assessment vs Audit

| Type | When | Purpose | Who |
|------|------|---------|-----|
| **Security Testing** | During development | Find vulnerabilities in code (SAST, DAST, pen test) | Developers, security team |
| **Security Assessment** | Ongoing / periodic | Evaluate security posture, identify risks | Internal team or consultants |
| **Security Audit** | Periodic / compliance | Verify compliance against policy/standard/regulation | Independent auditor |

| Aspect | Assessment | Audit |
|--------|------------|-------|
| Goal | "How secure are we?" | "Are we following the rules?" |
| Output | Recommendations | Pass/fail, findings report |
| Tone | Advisory | Formal, evidence-based |

**Exam tip:** Audit = compliance check against a baseline (policy, standard, regulation)

---

### Testing Types

| Abbrev | Full Name | Target | Access | Description |
|--------|-----------|--------|--------|-------------|
| **SAST** | Static Application Security Testing | Source code | White-box | Code review, analyzing codebase |
| **DAST** | Dynamic Application Security Testing | Running app | Black-box | Tests against compiled software |
| **IAST** | Interactive Application Security Testing | Running app | Gray-box | Interactive tests with agent inside app |
| **SCA** | Software Composition Analysis | Third-party libraries | — | CVE database check |

**Exam Traps:**
- SAST = **S**tatic = **S**ource code (not running)
- DAST = **D**ynamic = running app (not source)
- IAST = combines both (agent inside running app)

---

### CVSS vs CVE

| System | Purpose |
|--------|---------|
| **CVE** | Vulnerability identifier |
| **CVSS** | Severity score (0-10) |

**CVSS Metrics:** Base, Temporal, Environmental

---

### Web Application Attacks

| Attack | What Attacker Does | Goal | Example | Common Defense |
|--------|-------------------|------|---------|----------------|
| **CSRF** | Tricks victim's browser into making request | Perform action as victim | `<img src="bank.com/transfer?to=attacker">` | CSRF token, SameSite cookie |
| **XSS** | Injects JavaScript into page | Steal data, hijack session | `<script>steal(document.cookie)</script>` | Input validation, output encoding, CSP |
| **Directory Traversal** | Uses `../` to escape web folder | Read server files | `/file?path=../../../etc/passwd` | Input validation, whitelist paths |
| **SQL Injection** | Injects SQL into query | Access/modify database | `user=admin'--` bypasses login | Parameterized queries |
| **Command Injection** | Injects OS commands | Execute commands on server | `ping?host=;cat /etc/passwd` | Avoid shell, input validation |

---

### Security Attack Terms

**"War" Terms:**

| Term | What It Is |
|------|------------|
| **Wardriving** | Scanning for WiFi from a car |
| **Wardialing** | Auto-dialing phone numbers to find modems |
| **Warchalking** | Marking buildings to indicate WiFi availability |

**Social Engineering / Physical:**

| Term | What It Is |
|------|------------|
| **Tailgating** | Following someone through a secure door |
| **Piggybacking** | Same, but with person's knowledge/consent |
| **Shoulder surfing** | Watching someone type password |
| **Dumpster diving** | Searching trash for sensitive info |
| **Pretexting** | Fabricating scenario to extract info |
| **Baiting** | Leaving infected USB for victim to pick up |

**Phishing Family:**

| Term | Target |
|------|--------|
| **Phishing** | Mass email, anyone |
| **Spear phishing** | Targeted individual |
| **Whaling** | Executives (big fish) |
| **Vishing** | Voice/phone |
| **Smishing** | SMS text |

**Wireless Attacks:**

| Term | What It Is |
|------|------------|
| **Evil twin** | Fake AP mimicking legitimate one |
| **Rogue AP** | Unauthorized AP on network |
| **Bluejacking** | Sending unsolicited messages via Bluetooth |
| **Bluesnarfing** | Stealing data via Bluetooth |

**Other Exam Terms:**

| Term | What It Is |
|------|------------|
| **Salami attack** | Small thefts that add up (shaving pennies) |
| **Birthday attack** | Hash collision exploit (birthday paradox) |
| **Rainbow table** | Precomputed hash lookup table (defeated by salting) |
| **Pass the hash** | Using stolen hash without cracking it |
| **Watering hole** | Compromising site your target visits |
| **Typosquatting** | Registering misspelled domains (gooogle.com) |

---

## Physical Security

### Duress

Secret signal when under threat while appearing to comply.

| Scenario | Signal |
|----------|--------|
| Bank robbery | Silent alarm PIN |
| Hostage situation | Code phrase |
| Forced entry | Duress finger on biometric |

---

### Evidence Types

| Type | Description | Example |
|------|-------------|---------|
| **Direct/Real** | Proves fact directly | Video of crime |
| **Secondary** | Copy of original | Forensic disk image |
| **Corroborative** | Supports other evidence | Second witness |
| **Circumstantial** | Requires inference | Fingerprints at scene |

**Example (Hard Disk Theft):**

| Evidence | Type | Why |
|----------|------|-----|
| Stolen disk found in intruder's bag | Direct/Real | Physical proof |
| Forensic backup image of the disk | Secondary | Copy, not original |
| Second witness confirms first witness | Corroborative | Supports other evidence |
| Intruder's fingerprints in server room | Circumstantial | Proves presence, not action |

**Best Evidence Rule:** Courts prefer originals.

---

### Incident Management Framework (DRMRRRL)

| Step | Phase | What Happens |
|------|-------|--------------|
| **D** | Detect | Identify incident (alerts, logs, user reports) |
| **R** | Response | Assemble team, assess scope |
| **M** | Mitigate | Contain damage, isolate systems |
| **R** | Report | Notify stakeholders, management, regulators |
| **R** | Recovery | Restore systems to normal operation |
| **R** | Remediation | Fix root cause, patch vulnerabilities |
| **L** | Lessons Learned | Post-incident review, update procedures |

**Exam tips:**
- Lessons learned = always last
- Containment before recovery
- Reporting requirements depend on regulation (GDPR, HIPAA, etc.)

---

### Forensic Response Steps (Device Compromised)

| Step | Action | Why |
|------|--------|-----|
| 1 | **Isolate** — disconnect from network (NOT power) | Prevent spreading, preserve volatile evidence |
| 2 | **Capture volatile** — RAM dump, running processes, network connections | Most volatile, lost when powered off |
| 3 | **Power off** (if needed) | Stop malicious activity after volatile captured |
| 4 | **Use write blocker** — attach to disk | Prevent any changes to original disk |
| 5 | **Create forensic image** — bit-by-bit copy of disk | Preserves deleted files, slack space, metadata |
| 6 | **Hash original and copy** — SHA-256 | Prove integrity (hashes must match) |
| 7 | **Analyze the image only** — never the original | Original stays untouched for court |
| 8 | **Maintain chain of custody** — document who, when, how | Proves evidence not tampered |

**Order of Volatility (capture first → last):**

| Priority | Evidence | Volatility |
|----------|----------|------------|
| 1 | CPU registers, cache | Seconds |
| 2 | RAM | Minutes |
| 3 | Network connections | Minutes |
| 4 | Running processes | Minutes |
| 5 | Disk | Stable |
| 6 | Backups, logs | Stable |

---

### False Positive vs False Negative

- **False Positive** = Alert fired, no actual threat (false alarm)
- **False Negative** = No alert, real threat exists (missed detection) — **worse for security**

---

### Biometric Errors

| Metric | Full Name | Description |
|--------|-----------|-------------|
| **Type I / FRR** | False Rejection Rate | Legitimate user rejected |
| **Type II / FAR** | False Acceptance Rate | Imposter accepted |
| **CER / EER** | Crossover Error Rate | Point where FRR = FAR |

**Lower CER = better biometric system**

---

## Network Layers

### OSI vs TCP/IP

| OSI (7 layers) | TCP/IP (4 layers) |
|----------------|-------------------|
| 7 - Application | Application |
| 6 - Presentation | ↑ |
| 5 - Session | ↑ |
| 4 - Transport | Transport |
| 3 - Network | Internet |
| 2 - Data Link | Network Access |
| 1 - Physical | ↑ |

**Only exact match:** Transport layer

---

### Data Units by Layer (PDU)

| Layer | Data Unit |
|-------|-----------|
| 7-5 | Data |
| 4 | Segment (TCP) / Datagram (UDP) |
| 3 | Packet |
| 2 | Frame |
| 1 | Bits |

---

### Network Topologies

| Topology | Failure Impact | Redundancy | Modern Usage |
|----------|----------------|------------|--------------|
| **Star** | Center fails = all down | Low | Most common (LAN) |
| **Mesh** | Fault-tolerant | High | Data centers, cloud, WAN |
| **Hybrid** | Varies | Medium-High | Large enterprises |
| **Ring** | One break = down | Low | Legacy (SONET/fiber) |
| **Bus** | Cable break = down | None | Obsolete |
| **Tree** | Root fails = branches down | Low | Hierarchical networks |

**Exam tips:**
- Most fault-tolerant → Mesh
- Most common LAN → Star

---

### SDN (Software-Defined Networking)

| Concept | Description |
|---------|-------------|
| **Control Plane** | Decides where traffic goes |
| **Data Plane** | Moves traffic |
| **SDN Controller** | Central management (single point of failure) |
| **Northbound API** | Users/apps → Controller |
| **Southbound API** | Controller → Network devices |

**Example (Cloud VPC):**
```
YOU: gcloud compute firewall-rules create allow-ssh --allow tcp:22
                    │
                    │ NORTHBOUND (you → controller)
                    ↓
         GCP SDN CONTROLLER (processes request)
                    │
                    │ SOUTHBOUND (controller → infra)
                    ↓
         Physical/virtual switches now allow SSH
```

**Key:** SDN separates control plane from data plane.

---

### Routing Protocols

| Protocol | Type | Scope | Best Exam Answer |
|----------|------|-------|------------------|
| **RIP** | Distance-vector | Internal (IGP) | Small LAN (15 hop limit) |
| **OSPF** | Link-state | Internal (IGP) | Enterprise LAN/Campus |
| **EIGRP** | Hybrid | Internal (IGP) | Cisco enterprise |
| **IS-IS** | Link-state | Internal (IGP) | Large ISP backbone |
| **BGP** | Path-vector | External (EGP) | Internet (between ISPs) |

**Exam keywords:**
- IGP (Interior) = within organization (RIP, OSPF, EIGRP)
- EGP (Exterior) = between organizations/internet (BGP)
- LAN routing → OSPF or RIP
- Internet routing → BGP

**SDN:** OSPF-like routing functions move to centralized controller.

---

## NIST 800 Series

| Number | Topic |
|--------|-------|
| 800-30 | Risk Assessment |
| 800-34 | BCP/Contingency |
| 800-37 | RMF |
| 800-53 | Security Controls |
| 800-88 | Media Sanitization |

### NIST 800-37 RMF Steps (PCSIAAM)

| Step | Phase | What Happens |
|------|-------|--------------|
| 1 | **P**repare | Establish context, priorities, resources |
| 2 | **C**ategorize | Classify system based on impact (FIPS 199) |
| 3 | **S**elect | Choose security controls (from 800-53) |
| 4 | **I**mplement | Deploy the selected controls |
| 5 | **A**ssess | Test controls for effectiveness |
| 6 | **A**uthorize | Management accepts risk, grants ATO |
| 7 | **M**onitor | Ongoing monitoring and updates |

**Memory aid:** **P**eople **C**an **S**ee **I** **A**m **A**lways **M**onitoring

---

## Privacy Laws

| Law | Scope |
|-----|-------|
| **GLBA** (Gramm-Leach-Bliley) | Financial institutions |
| **HIPAA** | Healthcare |
| **FERPA** | Education (student records) |
| **COPPA** | Children under 13 online |
| **SOX** (Sarbanes-Oxley) | Public companies (financial reporting) |
| **ECPA** | Electronic communications |
| **Privacy Act of 1974** | Federal government |
| **GDPR** | EU residents' data |

---

## Quick Reference

1. Insurance = **Assignment**
2. Bell-LaPadula * = **No write down**
3. Biba * = **No write up**
4. Sag = **Momentary voltage drop**
5. Brownout = **Extended low voltage**
6. Class B suppression = **Halon/CO2**
7. Class K suppression = **Wet chemical**
8. Threat categories = **STRIDE**
9. Key exchange = **DH/ECDHE**
10. Bulk encryption = **AES**
11. Source code analysis = **SAST**
12. Library vulnerabilities = **SCA**
13. TPM location = **Motherboard**
14. Highest commercial EAL = **EAL4**
15. Vulnerability score = **CVSS**
