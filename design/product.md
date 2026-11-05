# Global Running App — Complete Feature Inventory

**Working names discussed:** Ije, Enyi, Vaa, Wego, Kintra, Relay, Runo, Stride. **AI engine working name:** PacePilot / RunSense.  
**Platform:** iOS-first, native SwiftUI.  
**Status:** Product concept and proposed roadmap; features are not asserted to be implemented.  
**Product promise:** A full-fledged running and workout app that people can use indefinitely **without depositing money, holding crypto, redeeming an offer, or participating in financial features**.

## 1. Core fitness and running

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| F01 | Start, pause, resume and finish a run | One-tap workout controls; usable while moving | SwiftUI, Core Location, Core Motion | P0 | Core concept |
| F02 | Live workout metrics | Distance, elapsed time, current/average pace and progress | Core Location, monotonic timers | P0 | Core concept |
| F03 | Cadence tracking | Current steps per minute and cadence trends | Core Motion `CMPedometer` when supported; watch sensors optional | P0 | Sensor precision varies by device placement |
| F04 | Workout history | Private records of completed runs and session summaries | SwiftData, optional HealthKit | P1 | On-device by default |
| F05 | Personal bests and goals | Target distance, time, pace and progressive goals | Local workout analytics | P1 | Concept |
| F06 | Route and elevation metrics | Optional map of the runner's own path and elevation | Core Location, MapKit | P1 | No automatic public route sharing |
| F07 | Fitness modes beyond running | Walking, cycling, general workouts in later releases | Activity-specific sensors and UI | P2 | Expansion, not MVP |
| F08 | Apple Health integration | Save workouts and read only authorized relevant health information | HealthKit | P1 | Requires opt-in authorization |
| F09 | Apple Watch support | Watch-based recording, heart rate, wrist feedback and workout sync | HealthKit workout APIs, watchOS, WatchConnectivity | P2 | Future enhancement; phone-only must work |
| F10 | Live workout on lock screen | Key metrics and controls when the phone is locked | ActivityKit Live Activities | P0–P1 | Lock-screen behavior needs device testing |
| F11 | Workout works without payments | Tracking and social features function without a wallet, treasury or sponsor | Independent fitness and social modules | P0 | Nonnegotiable product principle |

## 2. Passive encounters and social proximity

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| S01 | Passive nearby runner discovery | Detect another participating runner approaching without opening a map or tapping devices | Core Bluetooth BLE advertising/scanning | P0 | Defining interaction; locked-phone reliability must be proven |
| S02 | Encounter vibration | Short, subtle vibration when another runner is detected | UIKit haptics / Core Haptics as appropriate | P0 | Must avoid repeated alerts |
| S03 | Pass-by encounter | Two runners pass without speaking; encounter still counts | Local proximity event processing | P0 | No mutual introduction required |
| S04 | Optional human connection | Runners may choose to stop, say hello or connect later; never obligatory | Optional social interaction UI | P1–P2 | No forced identity exchange |
| S05 | Encounter counters | Show number of runners crossed, optionally first-time encounters | Local counting and deduplication | P0 | Counts, not identities, are the core social output |
| S06 | Rotating anonymous identifiers | Broadcast short-lived identifiers rather than permanent public identities | BLE protocol, local ephemeral credentials | P0 | Rotation and cross-device correlation require careful design |
| S07 | Deduplicate encounters | Prevent one nearby runner from incrementing repeatedly during one pass | Time windows, ephemeral session state | P0 | Approximate counts acceptable initially |
| S08 | Privacy-preserving encounter storage | Keep raw encounter events local and minimize retained records | On-device database, retention limits | P0 | No public social graph by default |
| S09 | Wi-Fi Aware discovery experiment | Investigate peer discovery where Wi-Fi offers a practical advantage | Network framework / Wi-Fi Aware on compatible iOS devices | Experimental | Not a proven replacement for passive BLE with locked devices |
| S10 | UWB proximity enhancement | Optional closer-range confirmation for compatible devices | Nearby Interaction | P2 / experimental | Device support and session setup constraints |
| S11 | Encounter and nearby-stop notification arbitration | Choose the most useful alert when several events occur | On-device priority rules | P1 | Prevent notification overload |

## 3. Places, merchants, clubs and events

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| M01 | Nearby merchant discovery | See participating restaurants, cafes, shops and service points near the current route | MapKit, Core Location, merchant backend | P0–P1 | Exact runner path need not be uploaded |
| M02 | Merchant enrollment | A restaurant or other business creates a participating location | Merchant web/mobile portal, verification | P1 | Fraud and payout destination checks needed |
| M03 | Merchant-defined offers | Merchant decides what can be redeemed on site: meals, drinks, snacks, discounts, experiences or other permitted items | Offer/catalog service | P0–P1 | **Not a water-only app** |
| M04 | Merchant controls availability | Merchants set available stock, redemption windows, limits and eligibility | Inventory and offer-management UI | P1 | No promise of unlimited items |
| M05 | Community-funded merchant redemption | Eligible runner approaches, validates claim and collects the listed item | QR first; NFC where supported; redemption backend and vault | P0 hackathon demo | Merchant must receive guaranteed/escrowed authorization before fulfilment |
| M06 | Tap-based merchant interaction | Tap phone/tag/device to open or claim an offer | Core NFC, supported tags / wallet flows | P1–P2 | iPhone NFC capabilities are more constrained than generic phone-to-phone BLE |
| M07 | QR fallback redemption | Scan/show a rotating code without special hardware | AVFoundation camera scanning, signed short-lived claims | P0 | Simpler first implementation |
| M08 | Merchant settlement dashboard | See validated redemptions and pending/completed payouts | Merchant portal, NEAR indexer/back end | P1 | Payout may be crypto first, fiat via partners later |
| M09 | Community-organized running events | Public 5K sessions, meetups, group workouts and races | Event directory, registration and scheduling | P1 | Events don't require financial participation |
| M10 | Social events and runners' parties | Discover or organize post-run gatherings and community celebrations | Event listings, venue profiles, optional RSVP | P1–P2 | Core social vision |
| M11 | Route-adjacent opportunities | Contextually surface a nearby eligible restaurant or event mid-run | MapKit and contextual notification engine | P1 | Must not distract from traffic or safety |
| M12 | Merchant-funded or sponsored experiences | Merchants/brands provide redeemables or support events | Offers, campaign attribution and payment rails | P1–P2 | Merchant sets the item and conditions |

## 4. Community funding and optional economics

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| C01 | Permissionless fitness participation | Anyone can join runs without depositing or applying to treasury membership | Standard app onboarding | P0 | Essential principle |
| C02 | Voluntary contributions | Runners or non-runners may contribute any amount they choose | NEAR-compatible funding flow and supported token swaps | P1 | Never required to exercise |
| C03 | Global sponsorship | Someone in Canada can support a running community or merchant in Lagos | NEAR Intents / supported settlement integrations | P1 | Cross-border fiat payouts require separate partners |
| C04 | Nonprofit/organization sponsors | NGOs, clubs and brands fund offerings or challenges | Campaign accounts, optional governance | P1 | Donor rules and reporting required |
| C05 | Community treasury | Shared pool supports merchant fulfilment and other approved community purposes | Smart contract vault | P0–P1 | Separate from user deposits |
| C06 | Earmarked contributions | Donors may allocate funds to cities, events, merchants, activities or categories | Campaign-specific vault allocations | P1 | Avoid silently redirecting restricted donations |
| C07 | Community-funded challenges | E.g. complete a 5K and unlock $5 in spending value | Challenge contracts, activity attestations | P1 | Must pre-fund and cap liabilities |
| C08 | Reward availability not guaranteed | App is useful with zero sponsors or zero offers | Product separation | P0 | No pay-to-participate expectations |
| C09 | Optional embedded wallet | Introduce wallet capabilities only for payment-related interactions | Embedded wallet or account abstraction UX | P1 | Zero wallet setup for regular workout user |
| C10 | Payment abstraction | Users/merchants need not understand NEAR to receive benefits | Sponsored transactions and backend orchestration where appropriate | P1 | Costs, custody model and compliance must be explicit |
| C11 | Confidential financial execution | Reduce visibility of supported cross-chain settlement details | NEAR Confidential Intents as supported | P1 / integration research | Does **not** automatically make arbitrary vault state, merchants or off-chain data invisible |
| C12 | Auditable donations without public identity exposure | Show funding usage while protecting personal donor information | Aggregated reporting, privacy-preserving accounting | P2 | Balance transparency and privacy carefully |

## 5. Shared treasury, multisig and policies

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| T01 | 1-of-many redemption initiation | Any eligible participant independently requests a valid merchant payment; no other runner must approve it | Permissionless vault method / membership eligibility | P0–P1 | **Not** unrestricted 1-of-N custody keys |
| T02 | Continuously growing membership | New runners gain eligibility without adding thousands of NEAR access keys to a multisig | Registry or proof-based policy | P1 | Membership alone need not imply spending right |
| T03 | No unrestricted pot control | No runner can withdraw arbitrary funds, change policy or spend to unknown recipients | Non-bypassable onchain checks | P0 | Fundamental security invariant |
| T04 | Verified merchant-only payouts | Treasury transfers only to registered/eligible destinations | Merchant registry and vault | P0 | Governance admission must resist fake merchants |
| T05 | Personal daily spend cap | Limit the value each eligible runner can redeem per day | Vault accounting | P0 | Denominated in consistent value units |
| T06 | Global daily treasury budget | Cap the day's total reserved plus spent amount | Vault policy | P0 | Prevent exhaustion through many individually valid claims |
| T07 | Per-merchant and per-offer limits | Bound exposure to any single shop/offer | Vault rules and inventory coordination | P1 | Optional later caps |
| T08 | Activity-based eligibility proof | Claim only after qualifying use of the app or verified challenge | Signed attestation / verifier | P0–P1 | Workout sensor data is not inherently cheat-proof |
| T09 | Replay-resistant redemption | A successful claim cannot be replayed | Nonces/nullifiers, one-time receipts | P0 | Atomic state transition and reconciliation needed |
| T10 | Funding reservations and failure recovery | Reserve amounts before claim, reconcile successful or failed payouts | Contract state machine | P0 | Asynchronous cross-contract operations need careful handling |
| T11 | SputnikDAO governance | Govern treasury parameters, funding allocations and roles | SputnikDAO | P1 | Separate M-of-N administration from 1-of-N redemption |
| T12 | Trezu treasury administration | Operator interface for proposals, signers and funds when compatible | Trezu | P1 / feasibility | Verify supported deployments and integration APIs |
| T13 | M-of-N admin authorization | Policies, merchant admissions, pause or upgrades need higher governance threshold | DAO governance / multisig | P1 | No direct bypass of spending protections |
| T14 | Emergency pause and recovery | Stop abuse or handle exploits with transparent rules | Restricted admin controls | P1 | Scope and fund recovery policy must be defined |
| T15 | Spend receipts and accountability | Record the minimum necessary proof of redemption and settlement outcome | Onchain events plus optional private records | P1 | Avoid linking identifiable workouts to public transfers |

## 6. Optional personal goal-lock deposits

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| G01 | Personal commitment vault | Runner optionally locks their **own** $10/$25/$50/etc. | Separate escrow contract | P2 | Never mingled with community treasury |
| G02 | Time-and-distance goal | Example: 5 km in under 30 minutes | Workout verification and goal parameters | P2 | Goals should be realistic and user-selected |
| G03 | Goal-based release | Unlock deposit when qualifying attempt is verified | Activity attestation + escrow policy | P2 | Cheating and disputes are material challenges |
| G04 | Retry window | Multiple attempts allowed within fixed window | Escrow deadline and attempt logic | Recommended design | Prefer fair release of money at deadline |
| G05 | Failure terms | Define refundable deadline, safe early exit, or separately consented donation | Explicit escrow policy | P2 | Avoid indefinite lockups or coercive forfeiture |
| G06 | Optional charity forfeiture | User can explicitly opt to donate a defined amount on failure | Escrow transfer with consent | Research only | Financial/gambling and charity rules may apply |
| G07 | Training toward commitment | Coach helps develop toward selected goal over multiple sessions | PacePilot, training plan | P2 | Never encourage running through pain/injury to protect a stake |

## 7. PacePilot — always-active *during a run* adaptive intelligence

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| A01 | Continuous workout-state engine | Maintain current state (warm-up, steady, accelerating, interval, recovery, cooldown) while run is active | Core Motion, Core Location, light Core ML/rules | P0 AI | Not an unrestricted 24/7 iOS background process |
| A02 | Personalized baseline | Learn typical pace/cadence at different efforts and goals | On-device historical analytics | P1 | Needs enough user data |
| A03 | Adaptive pace encouragement | Suggest a gentle increase when current target and observed effort permit it | Rules / Core ML | P0 AI | Cadence alone cannot prove user can safely go faster |
| A04 | Live cadence targets | Estimate sensible step-rate target and observe if runner is approaching it | `CMPedometer`, personal baseline | P0 AI | Not a universal fixed target like 180 spm |
| A05 | Rhythmic 1-2 audio guidance | Play "one, two, one, two" or beat at target step interval | `AVAudioEngine`, short voice samples | P0 AI | Precise audio generated locally, not token-by-token LLM |
| A06 | Maintain-target feedback | "That's your rhythm—hold it" and fade pacing beats when stable | Cadence state machine and speech | P0 AI | Limit interruptions |
| A07 | Recovery and slowdown prompts | Advise easing effort if trend suggests target is too strenuous | Pace trend, optional watch HR | P1 | No medical diagnosis; no unsafe pressure |
| A08 | Posture and attention cues | Occasional "look up," "relax shoulders" guidance | Contextual rule engine, audio | P1 | Phone sensors cannot actually verify head position |
| A09 | Comfortable breathing cues | Optional "breathe comfortably" or "settle your breath" | Audio cue engine | P1 | Do not prescribe restricting breathing |
| A10 | Nearby merchant audio | Mention a relevant registered stop or offer along the route | Merchant geospatial query + contextual audio | P1 | Avoid unsafe mid-road distractions |
| A11 | Encounter-aware audio priority | Combine social haptics with coaching without overlapping announcements | Notification/audio arbitration | P1 | Preserve quiet workout experience |
| A12 | On-device intelligent decisions | Use lightweight inference continuously; invoke generative explanation only as needed | Core ML; Foundation Models where supported | P1 | Works offline for basic coaching |
| A13 | Optional confidential advanced analysis | Opt-in aggregate workout insight using confidential AI | NEAR AI Cloud / TEE services as supported | P2 | Data leaves device even if protected in a TEE |
| A14 | Post-workout explanations | Explain pacing, consistency and workout progress in natural language | Local analytics; on-device language models | P1 | Secondary to live workout coaching |
| A15 | Coaching intensity preferences | Quiet, balanced, active coach | SwiftUI settings, state engine | P1 | User in control; can mute at any time |
| A16 | Adaptive training plan | Long-term targets and adjusted workout suggestions | History analytics / model | P2 | Later addition |
| A17 | Running form video analysis | Analyze an optional recorded clip of running mechanics | Vision/Core ML | P2 / research | Not an accurate clinical diagnosis from phone footage |
| A18 | Intelligent route suggestions | Route based on target distance, terrain and nearby stops | MapKit + vetted routing | P2 | Must not invent safe paths |
| A19 | Intelligent event recommendations | Recommend suitable events and clubs | Privacy-aware recommendation model | P2 | Never expose fitness profile to organizers by default |

## 8. Privacy, security and platform infrastructure

| ID | Feature | Experience / behavior | Proposed implementation | Priority | Status / caveats |
|---|---|---|---|---|---|
| P01 | Minimal data by design | No public runner identities, precise location streams or encounter graph | Local-first app architecture | P0 | Absolute zero off-chain data is incompatible with most cloud merchant/event services; define exactly what is processed |
| P02 | Local route and encounter privacy | Keep raw GPS routes and device encounters on device by default | SwiftData + data retention policy | P0 | User controls export/deletion |
| P03 | Approximate community location | Discover sessions/merchants without exposing live exact user location to other runners | Coarse queries, proximity search | P1 | Backend might still process coarse area |
| P04 | Separate financial privacy boundary | Workout identity is not unnecessarily linkable to settlement identity | Scoped credentials and minimal records | P1 | Compliance records may still be required |
| P05 | Device-bound credentials | Protect keys and redemption tokens | Keychain, Secure Enclave where supported | P1 | Device keys are not proof of movement |
| P06 | App authenticity checks | Raise cost of fake app requests | Apple App Attest | P1 | Doesn't prove 5K was run |
| P07 | Anti-spoofing and anti-collusion | Mitigate fake GPS workouts, repeat encounters, merchant/runner collusion | Motion consistency, signed challenges, caps, anomaly detection | P1 | Cannot be perfect with commodity phone sensors |
| P08 | Reliable background run behavior | Keep authorized workout tracking and proximity behavior active when screen locked | Core Location background modes, ActivityKit, Core Bluetooth background support | P0 | Must benchmark locked-device BLE and battery on physical iPhones |
| P09 | Battery and thermal budgets | Sensor duty cycles and contextual inference, not constant LLM execution | Native monitoring and profiling | P0–P1 | Run-time reliability is essential |
| P10 | Safe alerts | Haptics or spoken cues that don't demand the runner look at the phone | Core Haptics / UIKit, `AVAudioEngine`, speech | P0 | Safety-first notification policy |
| P11 | Offline-first exercise tracking | Continue workout without internet or blockchain availability | Local persistence and deferred sync | P0 | Payment/redemption may need connectivity |

## 9. Hackathon demo and rollout

| ID | Feature / milestone | What to show | Priority | Notes |
|---|---|---|---|---|
| D01 | Native iOS prototype | Start run, track distance/pace and show active session | P0 | SwiftUI, Core Motion, Core Location |
| D02 | Two-iPhone real encounter | Two locked iPhones pass; both vibrate and counters change | P0 | Run repeated device tests before broader build |
| D03 | Live adaptive cadence coach | Coach says increase tempo, plays 1-2 rhythm, detects target and fades guidance | P0 | Use real movement inputs, not fabricated demo metrics |
| D04 | Participating restaurant | Real mapped location with merchant-defined available items | P0 | One merchant is enough |
| D05 | Global donor + optional claim | Sponsor funds an item; eligible runner redeems; merchant sees payment | P0 | Testnet acceptable if clearly disclosed |
| D06 | Proof-enforced vault | Invalid claims fail, daily cap holds, approved merchant can receive payment | P0 | Demonstrate blocked cases as well as success |
| D07 | Events / runners' party | Create/view an event and show runner RSVPs or event listing | P1 | Can be simple for MVP |
| D08 | Drone-shot cinematic demo | Aerial run, live encounter, spoken coach, merchant discovery/redemption, community ending | P0 presentation | Include authentic screen recordings and transaction evidence |
| D09 | Technical uncut proof | Separate uninterrupted demo of actual app and settlement | P0 presentation | Helps judges distinguish editing from functional prototype |
| D10 | International scaling roadmap | Expand merchants, cities, clubs and workout categories after pilot | Later | Start with one physical community and one real merchant |

## 10. Core decisions and non-negotiables

| Decision | Agreed direction |
|---|---|
| Product category | Complete consumer fitness/workout app with social encounters, events and optional community commerce |
| Initial platform | iOS only, native SwiftUI |
| Main interaction | Run normally; nearby participating runners trigger subtle haptics and an encounter count |
| Social privacy | Passing does not require introduction, identity disclosure or persistent social relationship |
| Discovery | BLE-first; Wi-Fi Aware and UWB are experimental enhancements |
| Merchants | Merchant decides what can be redeemed; not restricted to water |
| Community funds | Optional deposits from anyone, including nonprofits and global donors |
| Treasury | Governed shared fund; no individual has unrestricted control |
| Spending | Any eligible runner may initiate a policy-valid merchant redemption, subject to caps and activity proof |
| Governance | SputnikDAO/Trezu are candidates for administrative governance, not per-purchase approval |
| Personal deposits | Optional separate goal-locked escrow; preference for retry/refund rather than punitive loss |
| AI | Continuously adaptive **during an active workout**, guiding cadence/pace through audio and haptics |
| Privacy claims | Minimize collection and use available confidential settlement; do **not** claim literally zero information exists off-chain or that every NEAR transaction is private |
| Defining promise | Users can enjoy the fitness app forever without touching payments or crypto |

## 11. Open questions to resolve before implementation

| Question | Why it matters |
|---|---|
| Can two locked iPhones discover each other reliably at running speed? | Core product feasibility; BLE background behavior must be tested |
| What precisely qualifies as one encounter? | Avoid counting people across streets or repeated meetings incorrectly |
| What evidence satisfies a monetary 5K challenge? | GPS, cadence and signed app records alone are not cheat-proof |
| Does the runner need to claim an item before visiting the merchant? | Impacts inventory reservation and checkout UX |
| How are merchants vetted and reimbursed, including fiat payouts? | Prevents fake-merchant draining and settlement failures |
| What can DAO governance change without bypassing hard spending rules? | Essential treasury trust boundary |
| Which confidential NEAR operations support the exact payment path? | Avoid assuming privacy for arbitrary contract transfers |
| What is the legal treatment of personal goal escrow and forfeiture? | Cross-border payments, consumer funds and possible gambling issues |
| What is the battery target for a 1–2 hour session? | Continuous BLE, location and cadence coaching can drain phones |
| What does the user explicitly consent to share? | Aligns privacy promises with actual backend, merchant and chain processing |

---

*This inventory includes both user-defined requirements and additional proposals discussed during ideation. Priority labels are planning recommendations, not confirmed commitments. Names, protocol integrations and platform APIs should be verified for compatibility during engineering.*
