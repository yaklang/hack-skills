# HACK.SKILLS - Hacker Arsenal for Agents

<p align="right">English | <a href="./README_CN.md">中文</a></p>

<p align="center">
    <img src="./assets/readme-hero-banner.jpg" alt="HackSkills Hero Banner" width="100%" />
</p>

<p align="center">
    <strong>Master Entry → Category Entries → Deep Topic Skills</strong><br/>
    One master entry, six category entries, and <strong>101</strong> deep topic skills across <strong>14 security domains</strong>.
</p>

An Agent Skills knowledge base covering web security, API security, authentication & authorization, OS privilege escalation (Linux/Windows/macOS), Active Directory attacks, mobile security, binary exploitation (Pwn), reverse engineering, cryptography attacks, blockchain & smart contract security, AI/ML & LLM security, network protocols & pivoting, and digital forensics — built for bug bounty, penetration testing, CTF competitions, and authorized security research.

The current branch has converged to a standard directory structure: every skill lives in its own directory, uniformly using `skills/{semantic-identifier}/SKILL.md`. The design goal is not to expose every minor tip as an entry point, but to compress what the loader truly needs to see into one master entry, six category entries, and deep topic skills drilled down on demand.

The objective is straightforward: organize security knowledge that is genuinely useful in real engagements and easy to audit and maintain into a set of installable, searchable, and composable HackSkills.

## Browse Online

- [OpenClaw Monitor](https://github.com/flik2002/openclaw-monitor) — Real-time AI agent monitoring dashboard for OpenClaw: tracks Gateway status, sessions, token usage & trends


This repo is published in three forms — pick whichever your workflow prefers; they are kept in sync on every push to `main`.

| Channel | What you get | When to use |
|---|---|---|
| **Web UI** — <https://skills.hackbenchmark.com> | Fuzzy search, category sidebar, P0/P1/P2 tier filter, copy-paste install commands, encrypted ZIP download | Quick lookup, sharing links to a specific skill, demoing the catalog |
| **GitHub source** — this repo | Plain `SKILL.md` per skill, full markdown rendering, pull-request review | Diff review, contributing, deep reading offline |
| **Encrypted ZIP** — see [Offline ZIP](#offline-zip-encrypted) | One-shot download of all `*.md` for air-gapped use | No internet on target, AV strips plain markdown |

The website is a static, fully client-side build of `site/` — no tracking, no backend. Source: [`site/`](./site), workflow: [`.github/workflows/deploy-pages.yml`](./.github/workflows/deploy-pages.yml). Search uses a weighted fuzzy index over name / id / category / description with field qualifiers like `category:auth`, `tier:deep`, `lines:>200`.

```text
                        ┌─────────────────────────────────────┐
                        │   skills.hackbenchmark.com (static) │  ── search / filter / copy install cmd
                        └─────────────────────────────────────┘
                                          ▲
   github.com/yaklang/hack-skills ───────►┤  same repo, three views
                                          ▼
                        ┌─────────────────────────────────────┐
                        │   hack-skills.zip (AES-256, public  │  ── offline / behind AV
                        │   password: hack-skills, via CDN)   │
                        └─────────────────────────────────────┘
```

## Knowledge Sources & Distillation Boundaries

This repository is not a mirror of external materials — it is a distillation layer aimed at Agents.

Primary reference sources (all publicly available, used strictly for educational distillation):

| Source | What It Provides | How We Use It |
|---|---|---|
| `swisskyrepo/PayloadsAllTheThings` | 64 vulnerability categories, payload families, bypass techniques, exploit chains | Distilled into scenario-based indices, method matrices, per-engine/per-database payload sections |
| `PentesterSpecialDict` | OS-specific payload dictionaries, Java middleware path fuzzing lists, file extension databases | Distilled into parameter naming patterns, endpoint frequency tables, middleware fingerprint matrices |
| `Dictionary-Of-Pentesting` | BugBounty bypass techniques (12 topics), cloud metadata endpoints, XXE payload collections, one-liner toolchains | Distilled into bypass pattern matrices, cloud metadata endpoint tables, WAF vendor bypass sections |
| `Hello-CTF` | CTF web security tutorials with hands-on tricks for PHP/Python/Java challenges | Distilled into CTF-specific technique sections (handler bypass, filter chain tricks, Flask PIN) |
| `ctf-wiki` | CTF competition knowledge base covering Pwn, Crypto, Reverse Engineering, Forensics, and Misc | Distilled into binary exploitation techniques (stack/heap/kernel), crypto attack patterns (RSA/lattice/symmetric), RE methodology, steganography, and traffic analysis skills |
| `hacktricks` | Penetration testing encyclopedia covering web tricks, Linux/Windows/macOS privilege escalation, Active Directory, containers, mobile, and AI security | Distilled into OS-specific privilege escalation playbooks, AD attack chains (Kerberos/ACL/ADCS), mobile pentesting checklists, container escape techniques, and network pivoting strategies |
| Public security research papers and CVE advisories | Methodology frameworks, vulnerability pattern taxonomies, statistical distributions | Distilled into attack pattern matrices, systematic testing checklists, decision trees |

Processing principles:

- No direct copying of large dictionaries or full payload lists.
- Prioritize distilling into routable, composable, and auditable security skills.
- Use small, stable samples, taxonomies, and cross-references to improve Agent stability in real security scenarios.
- No customer-specific information, no vendor-identifiable case details, purely educational methodology.

## Quick Start

The preferred entry point is `hack`:

```bash
npx skills add yaklang/hack-skills
```

If your tooling supports pulling a single SKILL.md directly, you can also use:

- frontmatter name: `hack`
- raw URL: `https://raw.githubusercontent.com/yaklang/hack-skills/main/skills/hack/SKILL.md`

After installing, the recommended order is simple: start from the master entry, then move into category entries, and only then drill into deep topic skills.

## Loader Priority

| Layer | Role | Recommended Exposure | Representative Skill |
|---|---|---|---|
| Master Entry | Global routing, test sequencing, cross-category switching | Expose first | [hack](./skills/hack/SKILL.md) |
| Category Entry | Route by attack surface to stable topic families | Expose first | [recon-for-sec](./skills/recon-for-sec/SKILL.md), [api-sec](./skills/api-sec/SKILL.md), [auth-sec](./skills/auth-sec/SKILL.md) |
| Deep Topic | Provide complete attack playbooks and execution details | Load on demand | [xss-cross-site-scripting](./skills/xss-cross-site-scripting/SKILL.md), [sqli-sql-injection](./skills/sqli-sql-injection/SKILL.md) |

## Main Entry Points

| Type | Skill | Purpose | When to Use First |
|---|---|---|---|
| Master Entry | [hack](./skills/hack/SKILL.md) | Global routing, phase assessment, cross-category switching | New target, unknown attack surface |
| Category Entry | [recon-for-sec](./skills/recon-for-sec/SKILL.md) | Asset discovery, technology identification | Just received the target |
| Category Entry | [api-sec](./skills/api-sec/SKILL.md) | REST, GraphQL, mobile backend routing | Observed API interfaces |
| Category Entry | [auth-sec](./skills/auth-sec/SKILL.md) | Authentication, sessions, OAuth, JWT, authorization | Login, tokens, object IDs |
| Category Entry | [injection-checking](./skills/injection-checking/SKILL.md) | XSS, SQLi, SSRF, XXE, SSTI, CMDi, NoSQL routing | Input enters interpreter |
| Category Entry | [file-access-vuln](./skills/file-access-vuln/SKILL.md) | Upload, download, LFI, path control | File operations |
| Category Entry | [business-logic-vuln](./skills/business-logic-vuln/SKILL.md) | Race conditions, pricing, workflow, state machines | Business process testing |

## Complete Skill Index (101 Skills)

### Reconnaissance & Methodology

| Skill | SKILL.md | SCENARIOS.md | Key Content |
|---|---|---|---|
| [hack](./skills/hack/SKILL.md) | 161 lines | - | Master router, phenomenon-to-skill mapping, expert intuitions |
| [recon-for-sec](./skills/recon-for-sec/SKILL.md) | 28 lines | - | Category router for reconnaissance phase |
| [recon-and-methodology](./skills/recon-and-methodology/SKILL.md) | 389 lines | - | Methodology framework, Java middleware fingerprint matrix, leak detection checklist |

### API Security

| Skill | SKILL.md | SCENARIOS.md | Key Content |
|---|---|---|---|
| [api-sec](./skills/api-sec/SKILL.md) | 48 lines | - | Category router for API testing |
| [api-recon-and-docs](./skills/api-recon-and-docs/SKILL.md) | 60 lines | - | API discovery, OpenAPI/Swagger, hidden endpoints |
| [api-authorization-and-bola](./skills/api-authorization-and-bola/SKILL.md) | 47 lines | - | BOLA/BFLA, mass assignment, object-level authz |
| [api-auth-and-jwt-abuse](./skills/api-auth-and-jwt-abuse/SKILL.md) | 75 lines | - | JWT attacks, API key abuse, token manipulation |
| [graphql-and-hidden-parameters](./skills/graphql-and-hidden-parameters/SKILL.md) | 49 lines | - | GraphQL introspection, batching, hidden param discovery |

### Authentication & Authorization

| Skill | SKILL.md | SCENARIOS.md | Key Content |
|---|---|---|---|
| [auth-sec](./skills/auth-sec/SKILL.md) | 40 lines | - | Category router for auth testing |
| [authbypass-authentication-flaws](./skills/authbypass-authentication-flaws/SKILL.md) | 441 lines | - | Password reset 22-pattern matrix, captcha bypass 20 methods, insecure randomness (UUID v1/mt_rand/ObjectId) |
| [jwt-oauth-token-attacks](./skills/jwt-oauth-token-attacks/SKILL.md) | 301 lines | - | JWT alg confusion, key confusion, claim tampering, JWKS abuse |
| [oauth-oidc-misconfiguration](./skills/oauth-oidc-misconfiguration/SKILL.md) | 45 lines | - | OAuth flow hijacking, OIDC misconfiguration |
| [saml-sso-assertion-attacks](./skills/saml-sso-assertion-attacks/SKILL.md) | 40 lines | - | SAML assertion manipulation, SSO bypass |
| [idor-broken-object-authorization](./skills/idor-broken-object-authorization/SKILL.md) | 336 lines | - | 8-category systematic IDOR testing, ORM filter chain leaks (Django/Prisma/Ransack) |

### Injection Attacks

| Skill | SKILL.md | SCENARIOS.md | Key Content |
|---|---|---|---|
| [injection-checking](./skills/injection-checking/SKILL.md) | 49 lines | - | Category router for injection testing |
| [xss-cross-site-scripting](./skills/xss-cross-site-scripting/SKILL.md) | 368 lines | 278 lines | Polyglot payloads, WAF bypass by vendor (Cloudflare/Akamai/Incapsula/WordFence), CSP bypass, DOM clobbering, CSS injection data exfiltration |
| [sqli-sql-injection](./skills/sqli-sql-injection/SKILL.md) | 475 lines | 575 lines | DB2/Cassandra/BigQuery/SQLite specifics, SQLite RCE, WAF bypass matrix, CTF techniques (handler/prepare/innodb) |
| [ssrf-server-side-request-forgery](./skills/ssrf-server-side-request-forgery/SKILL.md) | 314 lines | 226 lines | Cloud metadata 6-platform matrix, DNS rebinding, headless browser attacks, Gopher/Redis RCE chain |
| [ssti-server-side-template-injection](./skills/ssti-server-side-template-injection/SKILL.md) | 340 lines | 319 lines | 15+ engine coverage (Jinja2/Twig/Pug/Handlebars/EJS/Razor/EEx/Smarty), blind SSTI, Flask PIN calculation |
| [cmdi-command-injection](./skills/cmdi-command-injection/SKILL.md) | 494 lines | - | WAF bypass (wildcards/xor/base64), PHP disable_functions 6 bypass paths, component RCE (ImageMagick/FFmpeg/ES) |
| [nosql-injection](./skills/nosql-injection/SKILL.md) | 341 lines | - | Blind extraction automation scripts, duplicate key bypass, aggregation pipeline injection, $where JS execution |
| [xxe-xml-external-entity](./skills/xxe-xml-external-entity/SKILL.md) | 326 lines | 112 lines | Local DTD injection (17+ paths for Windows/Linux/JAR), blind XXE, Gopher/FTP OOB |
| [deserialization-insecure](./skills/deserialization-insecure/SKILL.md) | 714 lines | - | Java/PHP/Python + Ruby Marshal/YAML chains, .NET BinaryFormatter/ViewState/JSON.NET, Node.js node-serialize/funcster |
| [ghost-bits-cast-attack](./skills/ghost-bits-cast-attack/SKILL.md) | 400+ lines | PAYLOAD_COOKBOOK.md | Java char-to-byte narrowing WAF bypass (Black Hat Asia 2026): re-enables WAF-blocked SQLi/deser/upload/traversal/CRLF/smuggling across Tomcat/Spring/Jetty/Jackson/Fastjson/BCEL/HttpClient/Angus Mail; 255 Unicode bypass candidates per dangerous byte |
| [expression-language-injection](./skills/expression-language-injection/SKILL.md) | 243 lines | - | SpEL, OGNL, Java EL injection with RCE chains |
| [jndi-injection](./skills/jndi-injection/SKILL.md) | 265 lines | - | JNDI/LDAP/RMI exploitation, Log4Shell patterns |
| [crlf-injection](./skills/crlf-injection/SKILL.md) | 175 lines | - | Header injection, HTTP response splitting |
| [request-smuggling](./skills/request-smuggling/SKILL.md) | 298 lines | - | CL.TE/TE.CL/TE.TE with 8 obfuscation variants, HTTP/2 downgrade, client-side desync |
| [prototype-pollution](./skills/prototype-pollution/SKILL.md) | 190 lines | - | Express black-box probing keys, EJS/Kibana gadget chains, CVE-2019-7609 |
| [type-juggling](./skills/type-juggling/SKILL.md) | 291 lines | - | PHP loose comparison table, magic hash (MD5/SHA1/SHA256), HMAC 0e brute-force, CTF patterns |
| [http-parameter-pollution](./skills/http-parameter-pollution/SKILL.md) | 208 lines | - | Server behavior matrix (9 platforms), HPP+WAF bypass combos |
| [xslt-injection](./skills/xslt-injection/SKILL.md) | 281 lines | - | Three RCE chains (PHP/Java/.NET), EXSLT file write, vendor detection |
| [csv-formula-injection](./skills/csv-formula-injection/SKILL.md) | 144 lines | - | DDE/rundll32 payloads, Google Sheets IMPORT* exfiltration |

### File & Path Attacks

| Skill | SKILL.md | SCENARIOS.md | Key Content |
|---|---|---|---|
| [file-access-vuln](./skills/file-access-vuln/SKILL.md) | 32 lines | - | Category router for file access testing |
| [path-traversal-lfi](./skills/path-traversal-lfi/SKILL.md) | 603 lines | - | LFI-to-RCE 7 paths, PHP wrapper matrix (filter chains/oracle/phar), pearcmd 4 methods, parameter naming dictionary |
| [upload-insecure-files](./skills/upload-insecure-files/SKILL.md) | 287 lines | 158 lines | Success rate formula, editor path matrix, validation defect 5-dimension taxonomy, IIS/Apache/Nginx parsing tricks |

### Business Logic & Session

| Skill | SKILL.md | SCENARIOS.md | Key Content |
|---|---|---|---|
| [business-logic-vuln](./skills/business-logic-vuln/SKILL.md) | 32 lines | - | Category router for business logic testing |
| [business-logic-vulnerabilities](./skills/business-logic-vulnerabilities/SKILL.md) | 339 lines | 298 lines | Payment manipulation matrix (10 attacks), state machine bypass methodology, coupon/stock race |
| [race-condition](./skills/race-condition/SKILL.md) | 286 lines | - | TOCTOU model, HTTP/1.1 last-byte sync, HTTP/2 single-packet attack, Turbo Intruder templates, CVE-2022-4037 |
| [csrf-cross-site-request-forgery](./skills/csrf-cross-site-request-forgery/SKILL.md) | 324 lines | - | JSON CSRF 3 techniques, multipart upload CSRF, CSPT2CSRF modern variant |
| [clickjacking](./skills/clickjacking/SKILL.md) | 163 lines | - | Frame-based attacks, X-Frame-Options/CSP bypass |
| [cors-cross-origin-misconfiguration](./skills/cors-cross-origin-misconfiguration/SKILL.md) | 50 lines | 152 lines | Origin reflection, null origin, subdomain trust abuse |
| [open-redirect](./skills/open-redirect/SKILL.md) | 184 lines | - | Redirect chain abuse, tabnabbing (reverse tabnabbing) |
| [web-cache-deception](./skills/web-cache-deception/SKILL.md) | 211 lines | - | Path confusion, cache key manipulation |

### Advanced Web Security

| Skill | Key Content |
|---|---|
| [subdomain-takeover](./skills/subdomain-takeover/SKILL.md) | Dangling DNS records (CNAME/NS/A), cloud service fingerprinting, verification bypass, multi-provider takeover playbooks |
| [waf-bypass-techniques](./skills/waf-bypass-techniques/SKILL.md) | Encoding chains, chunked transfer tricks, HTTP smuggling for WAF evasion, vendor-specific bypass matrices (Cloudflare/AWS WAF/Akamai/ModSecurity) |
| [csp-bypass-advanced](./skills/csp-bypass-advanced/SKILL.md) | Script gadgets, base-uri abuse, JSONP callback injection, trusted CDN exploitation, CSP nonce/hash leak, strict-dynamic bypass |
| [http-host-header-attacks](./skills/http-host-header-attacks/SKILL.md) | Password reset poisoning, web cache poisoning via Host, routing-based SSRF, absolute-URL override tricks |
| [dangling-markup-injection](./skills/dangling-markup-injection/SKILL.md) | HTML injection for data exfiltration without JavaScript, img/form/base tag abuse, CSP-safe data theft |
| [dns-rebinding-attacks](./skills/dns-rebinding-attacks/SKILL.md) | DNS rebinding for internal network access, TTL manipulation, same-origin policy bypass, browser mitigation evasion |
| [email-header-injection](./skills/email-header-injection/SKILL.md) | SMTP header injection, CC/BCC manipulation, mail relay abuse, phishing via injected headers |
| [http2-specific-attacks](./skills/http2-specific-attacks/SKILL.md) | HTTP/2 request smuggling (H2.CL/H2.TE), HPACK header compression attacks, stream multiplexing abuse, HTTP/2→HTTP/1.1 downgrade |
| [prototype-pollution-advanced](./skills/prototype-pollution-advanced/SKILL.md) | Server-side gadget chain discovery, framework-specific PP→RCE (Express/Fastify/Next.js), AST injection, prototype poisoning in build tools |
| [401-403-bypass-techniques](./skills/401-403-bypass-techniques/SKILL.md) | Path normalization tricks, HTTP verb tampering, header-based bypass (X-Original-URL/X-Rewrite-URL), proxy misconfiguration, IP-based ACL evasion |

### Infrastructure & Network

| Skill | Key Content |
|---|---|
| [unauthorized-access-common-services](./skills/unauthorized-access-common-services/SKILL.md) | Service exposure checklist, reverse proxy misconfiguration (Nginx off-by-slash, X-Forwarded-For trust, Caddy template injection) |
| [insecure-source-code-management](./skills/insecure-source-code-management/SKILL.md) | .git/.svn/.hg/.bzr recovery, 403 vs 404 detection, backup file patterns |
| [dependency-confusion](./skills/dependency-confusion/SKILL.md) | npm/pip/gem public registry hijacking, manifest identification, scope/namespace defense |
| [websocket-security](./skills/websocket-security/SKILL.md) | CSWSH, Origin validation, wsrepl/ws-harness tooling |
| [network-protocol-attacks](./skills/network-protocol-attacks/SKILL.md) | ARP spoofing, DNS poisoning, LLMNR/NBT-NS poisoning, DHCP starvation, IPv6 attacks, protocol-level MitM |
| [tunneling-and-pivoting](./skills/tunneling-and-pivoting/SKILL.md) | SSH tunneling (local/remote/dynamic), SOCKS proxy chains, chisel/ligolo-ng, port forwarding, DNS/ICMP tunneling |
| [reverse-shell-techniques](./skills/reverse-shell-techniques/SKILL.md) | Multi-language shell generation, encrypted reverse shells (OpenSSL/ncat), staged/stageless payloads, firewall evasion, web shells |

### Linux & Container Security

| Skill | Key Content |
|---|---|
| [linux-privilege-escalation](./skills/linux-privilege-escalation/SKILL.md) | SUID/SGID abuse, kernel exploits, sudo misconfig, cron jobs, Linux Capabilities, writable service files, NFS no_root_squash |
| [container-escape-techniques](./skills/container-escape-techniques/SKILL.md) | Docker socket abuse, privileged container escape, cgroup breakout, runc vulnerabilities, mounted sensitive paths |
| [linux-security-bypass](./skills/linux-security-bypass/SKILL.md) | SELinux/AppArmor bypass, seccomp filter evasion, namespace abuse, LD_PRELOAD tricks |
| [linux-lateral-movement](./skills/linux-lateral-movement/SKILL.md) | SSH key harvesting, credential reuse, service exploitation, NFS/shared mount abuse, cron-based persistence |
| [kubernetes-pentesting](./skills/kubernetes-pentesting/SKILL.md) | Pod security policy bypass, RBAC abuse, ServiceAccount token theft, etcd access, container image backdoors, kubelet API |

### Windows & Active Directory

| Skill | Key Content |
|---|---|
| [windows-privilege-escalation](./skills/windows-privilege-escalation/SKILL.md) | Token manipulation, service misconfig, DLL hijacking, UAC bypass, AlwaysInstallElevated, unquoted service paths, PrintSpoofer/Potato |
| [active-directory-kerberos-attacks](./skills/active-directory-kerberos-attacks/SKILL.md) | Kerberoasting, AS-REP Roasting, Golden/Silver Ticket, delegation abuse (unconstrained/constrained/RBCD), Diamond Ticket |
| [active-directory-acl-abuse](./skills/active-directory-acl-abuse/SKILL.md) | ACL/DACL exploitation, DCSync, object ownership abuse, WriteDACL/GenericAll/GenericWrite attack paths, BloodHound integration |
| [active-directory-certificate-services](./skills/active-directory-certificate-services/SKILL.md) | ESC1–ESC8 attack patterns, certificate template abuse, PKINIT exploitation, Shadow Credentials, CA persistence |
| [ntlm-relay-coercion](./skills/ntlm-relay-coercion/SKILL.md) | PetitPotam, PrinterBug, NTLM relay chains, coercion techniques, WebDAV relay, NTLM downgrade |
| [windows-lateral-movement](./skills/windows-lateral-movement/SKILL.md) | PsExec, WMI, WinRM, DCOM, Pass-the-Hash/Pass-the-Ticket, RDP hijacking, scheduled tasks, service deployment |
| [windows-av-evasion](./skills/windows-av-evasion/SKILL.md) | AMSI bypass, ETW patching, API unhooking, shellcode loaders, Living-off-the-Land (LOLBins), payload encryption/obfuscation |

### macOS Security

| Skill | Key Content |
|---|---|
| [macos-security-bypass](./skills/macos-security-bypass/SKILL.md) | Gatekeeper bypass, TCC abuse, SIP/AMFI considerations, LaunchAgent/LaunchDaemon persistence, quarantine flag evasion |
| [macos-process-injection](./skills/macos-process-injection/SKILL.md) | Dylib injection/hijacking, task_for_pid, XPC exploitation, Electron app injection, DYLD_INSERT_LIBRARIES |

### Mobile Security

| Skill | Key Content |
|---|---|
| [android-pentesting-tricks](./skills/android-pentesting-tricks/SKILL.md) | APK analysis & reverse engineering, Frida hooking, Intent exploitation, root detection bypass, Content Provider leaks, WebView attacks |
| [ios-pentesting-tricks](./skills/ios-pentesting-tricks/SKILL.md) | IPA analysis, Objective-C runtime manipulation, jailbreak detection bypass, Keychain access, URL scheme abuse, binary protections |
| [mobile-ssl-pinning-bypass](./skills/mobile-ssl-pinning-bypass/SKILL.md) | Certificate pinning bypass for Android/iOS, Frida/Objection scripts, dynamic instrumentation, network security config manipulation |

### Binary Exploitation (Pwn)

| Skill | Key Content |
|---|---|
| [stack-overflow-and-rop](./skills/stack-overflow-and-rop/SKILL.md) | Buffer overflow, ROP chain construction, ret2libc, SROP (Sigreturn-Oriented Programming), stack pivoting, one-gadget |
| [heap-exploitation](./skills/heap-exploitation/SKILL.md) | Use-after-free, double free, tcache poisoning, fastbin attack, House of series techniques, safe-linking bypass |
| [format-string-exploitation](./skills/format-string-exploitation/SKILL.md) | Format string read/write primitives, GOT overwrite, arbitrary address write, FORTIFY_SOURCE bypass |
| [kernel-exploitation](./skills/kernel-exploitation/SKILL.md) | Kernel ROP, ret2usr, SMEP/SMAP/KPTI bypass, kernel race conditions, modprobe_path overwrite, msg_msg exploitation |
| [browser-exploitation-v8](./skills/browser-exploitation-v8/SKILL.md) | V8 engine exploitation, JIT compilation bugs, type confusion, OOB read/write, sandbox escape chains, wasm abuse |
| [sandbox-escape-techniques](./skills/sandbox-escape-techniques/SKILL.md) | Browser sandbox escape, seccomp bypass, IPC abuse, kernel exploitation for sandbox breakout, policy file manipulation |
| [binary-protection-bypass](./skills/binary-protection-bypass/SKILL.md) | ASLR/NX/PIE/Canary/Full RELRO bypass techniques, information leak exploitation, partial overwrite, GOT dereference |
| [arbitrary-write-to-rce](./skills/arbitrary-write-to-rce/SKILL.md) | Write primitive to code execution (GOT/__free_hook/__malloc_hook), FSOP, _IO_FILE exploitation, exit handler overwrite |

### Reverse Engineering

| Skill | Key Content |
|---|---|
| [anti-debugging-techniques](./skills/anti-debugging-techniques/SKILL.md) | ptrace detection, timing checks, self-modifying code, anti-VM techniques, debug flag inspection, exception-based anti-debug |
| [code-obfuscation-deobfuscation](./skills/code-obfuscation-deobfuscation/SKILL.md) | Control flow flattening, opaque predicates, string encryption, obfuscation tool analysis (OLLVM/Themida/VMProtect), automated deobfuscation |
| [symbolic-execution-tools](./skills/symbolic-execution-tools/SKILL.md) | angr, Z3, Triton for automated vulnerability discovery, constraint solving, path exploration, concolic execution |
| [vm-and-bytecode-reverse](./skills/vm-and-bytecode-reverse/SKILL.md) | Custom VM/bytecode analysis, Python/Java/.NET decompilation, VM handler reconstruction, opcode mapping |

### Cryptography Attacks

| Skill | Key Content |
|---|---|
| [rsa-attack-techniques](./skills/rsa-attack-techniques/SKILL.md) | Wiener attack, Boneh-Durfee, Hastad broadcast, common modulus, Coppersmith (small roots), Franklin-Reiter, padding oracle (PKCS#1 v1.5) |
| [symmetric-cipher-attacks](./skills/symmetric-cipher-attacks/SKILL.md) | Padding oracle (CBC), bit-flipping, ECB cut-and-paste, meet-in-the-middle, known-plaintext, IV reuse exploitation |
| [lattice-crypto-attacks](./skills/lattice-crypto-attacks/SKILL.md) | LLL/BKZ lattice reduction, Hidden Number Problem, NTRU attacks, CVP/SVP solving, knapsack cryptosystem attacks |
| [hash-attack-techniques](./skills/hash-attack-techniques/SKILL.md) | Length extension attack, birthday attack, hash collision exploitation, bcrypt/scrypt/argon2 analysis, HMAC timing |
| [classical-cipher-analysis](./skills/classical-cipher-analysis/SKILL.md) | Frequency analysis, Vigenère/Kasiski, Hill cipher, substitution cipher, transposition cipher, Enigma-style analysis, automated solving |

### Blockchain & Smart Contract

| Skill | SKILL.md | Supplementary | Key Content |
|---|---|---|---|
| [smart-contract-vulnerabilities](./skills/smart-contract-vulnerabilities/SKILL.md) | 314 lines | 460 lines | Reentrancy (4 variants), integer overflow, delegatecall storage collision, signature replay, CREATE2 exploitation, flash loan patterns |
| [defi-attack-patterns](./skills/defi-attack-patterns/SKILL.md) | 355 lines | - | Flash loan oracle manipulation, MEV sandwich/JIT/liquidation, first depositor vault attack, governance flash borrow, bridge exploits, fee-on-transfer tokens |

### AI/ML & LLM Security

| Skill | SKILL.md | Supplementary | Key Content |
|---|---|---|---|
| [llm-prompt-injection](./skills/llm-prompt-injection/SKILL.md) | 357 lines | 306 lines | Direct/indirect injection, RAG poisoning, tool/function abuse, markdown exfiltration, MCP security risks, encoding bypass |
| [ai-ml-security](./skills/ai-ml-security/SKILL.md) | 425 lines | - | Pickle RCE in model files, adversarial examples (FGSM/PGD/C&W), training data poisoning, model extraction, membership inference, agent security |

### Forensics & Steganography

| Skill | Key Content |
|---|---|
| [memory-forensics-volatility](./skills/memory-forensics-volatility/SKILL.md) | Volatility framework, process/module analysis, network artifact extraction, malware detection, registry hive analysis, timeline reconstruction |
| [steganography-techniques](./skills/steganography-techniques/SKILL.md) | LSB extraction, file format analysis, audio/image stego tools (zsteg/stegsolve/steghide), EXIF metadata, multi-layer embedding |
| [traffic-analysis-pcap](./skills/traffic-analysis-pcap/SKILL.md) | Wireshark/tshark analysis, protocol dissection, data extraction from captures, encrypted traffic identification, stream reconstruction |

## Skill Selection Guide

| Symptom | Recommended Entry | Notes |
|---|---|---|
| New target, insufficient information | [recon-for-sec](./skills/recon-for-sec/SKILL.md) | Start with methodology and asset understanding |
| REST API, GraphQL, mobile backend | [api-sec](./skills/api-sec/SKILL.md) | Route to recon, authz, token, or GraphQL |
| Login, password reset, 2FA, JWT, OAuth | [auth-sec](./skills/auth-sec/SKILL.md) | Distinguish auth, authz, and protocol config |
| HTML/JS reflection, template expressions | [injection-checking](./skills/injection-checking/SKILL.md) | Determine XSS, SQLi, SSRF, XXE, SSTI first |
| File paths, downloads, uploads | [file-access-vuln](./skills/file-access-vuln/SKILL.md) | Distinguish LFI/Traversal from Upload |
| Coupons, payments, state machines | [business-logic-vuln](./skills/business-logic-vuln/SKILL.md) | Model by business rules and race conditions |
| HTTP parsing anomalies | [request-smuggling](./skills/request-smuggling/SKILL.md) | Front/back-end framing disagreement |
| Node.js `__proto__` controllable | [prototype-pollution](./skills/prototype-pollution/SKILL.md) | Client-side PP→XSS, Server-side PP→RCE |
| PHP weak comparison, 0e hash | [type-juggling](./skills/type-juggling/SKILL.md) | Loose comparison auth bypass |
| .git/.svn/.env path accessible | [insecure-source-code-management](./skills/insecure-source-code-management/SKILL.md) | Source code recovery |
| Internal package names in manifests | [dependency-confusion](./skills/dependency-confusion/SKILL.md) | Supply chain hijacking |
| WebSocket protocol upgrade | [websocket-security](./skills/websocket-security/SKILL.md) | CSWSH and WS injection |
| CSV/Excel export functionality | [csv-formula-injection](./skills/csv-formula-injection/SKILL.md) | DDE injection in exports |
| One-time operations (coupons, rewards) | [race-condition](./skills/race-condition/SKILL.md) | Limit-overrun via concurrent requests |
| Smart contract, Solidity, EVM audit | [smart-contract-vulnerabilities](./skills/smart-contract-vulnerabilities/SKILL.md) | Reentrancy, overflow, access control, delegatecall |
| DeFi protocol, flash loan, oracle, MEV | [defi-attack-patterns](./skills/defi-attack-patterns/SKILL.md) | Flash loan, sandwich, governance, bridge |
| LLM, chatbot, prompt injection, RAG | [llm-prompt-injection](./skills/llm-prompt-injection/SKILL.md) | Direct/indirect injection, tool abuse, MCP |
| ML model, adversarial, model poisoning | [ai-ml-security](./skills/ai-ml-security/SKILL.md) | Supply chain, adversarial examples, extraction, agents |
| WAF blocking payloads | [waf-bypass-techniques](./skills/waf-bypass-techniques/SKILL.md) | Encoding, chunked transfer, vendor-specific evasion |
| Subdomain dangling CNAME/DNS | [subdomain-takeover](./skills/subdomain-takeover/SKILL.md) | Cloud service takeover, NS delegation hijacking |
| CSP blocking XSS execution | [csp-bypass-advanced](./skills/csp-bypass-advanced/SKILL.md) | Script gadgets, JSONP, trusted CDN, strict-dynamic |
| 401/403 on target endpoint | [401-403-bypass-techniques](./skills/401-403-bypass-techniques/SKILL.md) | Path normalization, verb tampering, header tricks |
| HTTP/2 protocol endpoint | [http2-specific-attacks](./skills/http2-specific-attacks/SKILL.md) | H2 smuggling, HPACK abuse, downgrade attacks |
| Linux host, SUID/sudo present | [linux-privilege-escalation](./skills/linux-privilege-escalation/SKILL.md) | Kernel, SUID, cron, capabilities, services |
| Docker/Kubernetes environment | [container-escape-techniques](./skills/container-escape-techniques/SKILL.md) | Docker socket, privileged escape, cgroup breakout |
| Kubernetes cluster access | [kubernetes-pentesting](./skills/kubernetes-pentesting/SKILL.md) | RBAC abuse, SA token, etcd, pod security bypass |
| Windows host, local admin needed | [windows-privilege-escalation](./skills/windows-privilege-escalation/SKILL.md) | Token, service, DLL hijack, UAC, Potato attacks |
| Active Directory, domain joined | [active-directory-kerberos-attacks](./skills/active-directory-kerberos-attacks/SKILL.md) | Kerberoast, AS-REP roast, Golden/Silver Ticket |
| AD CS, certificate templates | [active-directory-certificate-services](./skills/active-directory-certificate-services/SKILL.md) | ESC1–ESC8, template abuse, Shadow Credentials |
| NTLM hash, relay opportunity | [ntlm-relay-coercion](./skills/ntlm-relay-coercion/SKILL.md) | PetitPotam, PrinterBug, relay chains |
| Windows AV/EDR blocking execution | [windows-av-evasion](./skills/windows-av-evasion/SKILL.md) | AMSI bypass, unhooking, LOLBins, payload obfuscation |
| macOS endpoint access | [macos-security-bypass](./skills/macos-security-bypass/SKILL.md) | Gatekeeper, TCC, SIP considerations |
| Android/iOS application testing | [android-pentesting-tricks](./skills/android-pentesting-tricks/SKILL.md) | APK analysis, Frida, Intent, root detection bypass |
| SSL pinning blocking proxy | [mobile-ssl-pinning-bypass](./skills/mobile-ssl-pinning-bypass/SKILL.md) | Frida/Objection scripts, dynamic instrumentation |
| Binary/ELF/PE exploitation | [stack-overflow-and-rop](./skills/stack-overflow-and-rop/SKILL.md) | Buffer overflow, ROP, ret2libc, SROP |
| Heap corruption, UAF | [heap-exploitation](./skills/heap-exploitation/SKILL.md) | tcache/fastbin attacks, House of techniques |
| Kernel-level exploitation | [kernel-exploitation](./skills/kernel-exploitation/SKILL.md) | Kernel ROP, SMEP/SMAP bypass, modprobe_path |
| Browser 0-day, V8/JSC | [browser-exploitation-v8](./skills/browser-exploitation-v8/SKILL.md) | JIT bugs, type confusion, sandbox escape |
| Obfuscated/packed binary | [code-obfuscation-deobfuscation](./skills/code-obfuscation-deobfuscation/SKILL.md) | Control flow, opaque predicates, VM protection |
| CTF crypto challenge (RSA) | [rsa-attack-techniques](./skills/rsa-attack-techniques/SKILL.md) | Wiener, Coppersmith, common modulus, padding oracle |
| CTF crypto challenge (AES/DES) | [symmetric-cipher-attacks](./skills/symmetric-cipher-attacks/SKILL.md) | Padding oracle, bit-flip, ECB mode attacks |
| CTF crypto challenge (lattice) | [lattice-crypto-attacks](./skills/lattice-crypto-attacks/SKILL.md) | LLL/BKZ, Hidden Number Problem, knapsack |
| CTF classical cipher | [classical-cipher-analysis](./skills/classical-cipher-analysis/SKILL.md) | Frequency analysis, Vigenère, substitution |
| Memory dump analysis | [memory-forensics-volatility](./skills/memory-forensics-volatility/SKILL.md) | Volatility, process/network analysis, malware detect |
| Hidden data in images/audio | [steganography-techniques](./skills/steganography-techniques/SKILL.md) | LSB, format analysis, stego tools |
| PCAP traffic capture | [traffic-analysis-pcap](./skills/traffic-analysis-pcap/SKILL.md) | Wireshark, protocol dissection, stream extraction |
| Need to pivot through network | [tunneling-and-pivoting](./skills/tunneling-and-pivoting/SKILL.md) | SSH tunnel, SOCKS proxy, chisel/ligolo-ng |
| Need reverse shell on target | [reverse-shell-techniques](./skills/reverse-shell-techniques/SKILL.md) | Multi-language shells, encrypted, staged payloads |

## Installation

### General Installation

```bash
npx skills add yaklang/hack-skills
```

### Raw URL Installation

```bash
curl -fsSL https://raw.githubusercontent.com/yaklang/hack-skills/main/skills/hack/SKILL.md
```

### Local Use as a Knowledge Base

```bash
git clone https://github.com/yaklang/hack-skills.git
cd hack-skills
```

### Offline ZIP (encrypted)

For air-gapped environments, slow networks, or any place where AV / EDR / browser content scanners strip plain offensive-security markdown:

```bash
curl -fsSLO https://oss-qn.yaklang.com/hack-skills/latest/hack-skills.zip
7z x -phack-skills hack-skills.zip
# or:  unzip -P hack-skills hack-skills.zip
```

| Channel | URL |
|---|---|
| Primary CDN | <https://oss-qn.yaklang.com/hack-skills/latest/hack-skills.zip> |
| Backup CDN | <https://aliyun-oss.yaklang.com/hack-skills/latest/hack-skills.zip> |
| Build version manifest | <https://oss-qn.yaklang.com/hack-skills/latest/version.txt> |

**About the password.** The ZIP is wrapped with **AES-256** and a **public constant** password `hack-skills`. This is **not access control** — anyone can download, anyone can extract, the password is printed openly in the README, the website, the GitHub Actions workflow, and CI logs. It exists solely to bypass content heuristics on AV / EDR / browser scanners that flag plain offensive markdown and silently drop or quarantine the file in transit. Build, encryption settings, and integrity verification all live in [`.github/workflows/upload-hack-skills.yml`](./.github/workflows/upload-hack-skills.yml).

Same ZIP is also surfaced one-click on the website's nav bar (`ZIP` button) and the `Install → Offline ZIP` tab.

## Design Principles

- Security knowledge takes priority over fancy packaging.
- Content auditability takes priority over quantity expansion.
- Prioritize authorized testing, legitimate research, and defensive verification scenarios.
- Directory names should convey security semantics at a glance.
- No customer-specific information; all content is generic methodology for educational use.

## Contributing

PRs are welcome. Key areas include:

- New vulnerability categories and high-value cases
- Better bug bounty and penetration testing methodologies
- OS-specific privilege escalation paths and AD attack chains
- CTF challenge techniques (Pwn, Crypto, RE, Forensics)
- Edge conditions that Agents easily overlook
- Risk annotations, terminology consistency, and content denoising

Contributions should ideally be verifiable, auditable, and helpful for Agents to reason and execute more robustly in real tasks.
