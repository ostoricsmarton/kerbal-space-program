# Mission Context and Task Description

## Background

A European university research consortium plans to launch a series of small satellites as secondary payloads aboard commercial launch vehicles. These satellites follow the **CubeSat standard**, a widely adopted approach for low-cost space missions used by universities, startups, and research organizations.

CubeSats are modular nanosatellites composed of standardized units (“U”). One unit (1U) corresponds to a cube approximately 10 × 10 × 10 cm. In this assignment, all teams design a **3U CubeSat**, meaning a spacecraft approximately three units long.

The consortium intends to demonstrate that a relatively small engineering team can design complex space systems using modern **Model-Based Systems Engineering (MBSE)** practices. Student teams act as contracted systems engineering groups, responsible for defining the architecture for a single satellite mission.

The goal of the assignment is not to specialize in aerospace. Instead, it is to practice:

- requirements interpretation,
- architectural reasoning,
- behavioral modeling,
- traceability,
- and engineering justification under constraints.

Reasonable engineering assumptions may be used when information is incomplete, provided they are explicitly documented in the model.

## Mission Overview

Each team will receive one assigned mission variant.

Although the missions share similar technical foundations, each has distinct operational priorities and stakeholder expectations.

The satellite will operate in **Low Earth Orbit (LEO)**, typically at altitudes between 450 and 600 km. At this altitude, the spacecraft repeatedly moves into and out of sunlight during each orbit. These eclipse periods limit power generation and strongly influence operational planning.

The expected operational lifetime is approximately 18–36 months.

The satellite must function largely autonomously because communication opportunities with ground operators are limited to short visibility windows when the satellite passes over a ground station.

## Mission: Radio Network Node (RN)

The Radio Network Node mission acts as a communications relay.

The satellite receives radio messages from ground users or sensors, temporarily stores them, and forwards them later when a suitable downlink opportunity becomes available.

Typical challenges include:

- balancing receiver availability with limited power,
- managing message storage,
- and complying with radio communication regulations.

## Platform Concept

Regardless of mission type, the satellite consists of two main parts:

1. **Satellite Platform (Bus)** — the reusable infrastructure required to operate in space.
2. **Payload** — mission-specific equipment.

Students must design the architecture allocating system functions to platform elements such as:

- onboard computer,
- electrical power subsystem,
- communication radios,
- sensors and actuators,
- data storage,
- payload interfaces.

Teams are expected to use commercially available CubeSat components where possible. Exact hardware selection may later be estimated using publicly available supplier catalogues.

The focus of the assignment is architectural design rather than detailed hardware engineering.

## Operational Expectations

The spacecraft must:

- survive launch and deployment,
- operate autonomously between ground contacts,
- maintain safe operating conditions,
- execute mission activities,
- and support remote monitoring and commanding.

Students must model:

- functional decomposition,
- allocation of functions to subsystems,
- operational modes,
- and selected behavioral aspects such as scheduling, fault handling, or operational workflows.

Behavioral modeling may include:

- state machines,
- activity diagrams,
- or sequence diagrams.

Teams must also define verification approaches and demonstrate analysis of at least one engineering concern, such as safety, reliability, performance, or functional correctness.

## Important Terminology

The requirements use several technical terms common in space systems engineering.

**Payload**  
Mission-specific equipment performing the primary purpose of the satellite (camera, radio relay hardware, or experiment module).

**Satellite Bus (Platform)**  
Reusable subsystems required for spacecraft operation independent of mission objectives, including power generation, computing, and communications.

**Low Earth Orbit (LEO)**  
An orbit relatively close to Earth. Satellites periodically enter Earth’s shadow, preventing solar power generation during eclipse periods.

**Ground Station**  
A terrestrial communication facility used to send commands and receive telemetry or mission data.

**Telemetry**  
Status information transmitted from the satellite to operators, such as temperatures, battery state, or subsystem health.

**Commanding**  
Instructions transmitted from ground operators to control spacecraft behavior.

**Safe Mode**  
A protective operational configuration entered when faults occur. Nonessential activities stop while core survival functions remain active.

**Commercial Off‑The‑Shelf (COTS) Components**  
Standardized products available commercially rather than custom-designed hardware.

**Secondary Payload**

A spacecraft launched together with a primary mission. Secondary payloads must comply with the strict safety and operational constraints set by the launch provider.

## Engineering Assumptions

Students are not expected to possess specialist aerospace knowledge.

Teams may:

- make reasonable engineering assumptions,
- simplify orbital mechanics considerations,
- or define missing numerical parameters when necessary.

All assumptions must be documented and traceable within the model.

The objective is a coherent, well-justified architecture rather than technical perfection.

# Stakeholder Inputs

## Collected Meeting Notes and Communication Extracts

The following excerpts summarize discussions with representatives of organizations involved in the CubeSat program. These notes were recorded by project coordinators and may contain informal language, assumptions, or partial viewpoints. The chief engineer reviewed the memos and left additional comments and directions.

Student teams are responsible for identifying stakeholders, interpreting concerns, and formalizing requirements where appropriate.

## Memo A — Program Funding Review Meeting

We need to keep expectations realistic. This is supposed to demonstrate repeatable missions, not a one-off engineering science project. If every team designs custom electronics, the costs will explode, and integration will become impossible.

We strongly prefer existing CubeSat modules wherever possible. Suppliers already provide avionics stacks, radios, power systems, etc. Use those unless there is a very strong argument not to.

Also, remember this is a small satellite. We are not paying for redundant spacecraft unless somebody can clearly explain why the mission would otherwise fail. The overall hardware budget must stay within a university-scale project — think well below flagship research satellite costs.

***Engineering review comments:***

- *Prefer commercially available CubeSat subsystems (OBC, EPS, radios, sensors).*
- *Typical subsystem cost range ≈ €5k–€40k.*
- *Hardware redundancy uncommon in 3U missions; software recovery preferred.*
- *Assume total hardware budget ≈ €200k (order of magnitude).*

## Memo B — Launch Integration Coordination Call

The launch broker reminded us again that secondary payloads are tolerated only as long as they behave predictably. Anything unsafe delays the entire launch campaign.

The satellite must fit inside a standard deployer. Please do not assume extra volume or protruding elements unless they remain stowed.

The biggest concern is activation during launch. Radios or powered systems activating early are unacceptable. There must be a clear transition between the launch configuration and the operational configuration after deployment.

Assume there will be a deployment confirmation signal or timer before anything active happens.

***Engineering review comments:***

- *Assume standard 3U envelope (~10 × 10 × 34 cm).*
- *No protrusions during launch; deployables allowed afterward.*
- *Multiple deployment inhibits expected (mechanical switch + timer or software condition).*
- *RF transmission activation delayed after deployment (timer on the order of tens of minutes).*

## Memo C — Regulatory Consultation Summary

Frequency licensing is not optional. Whoever operates the radio must be able to configure transmission parameters in accordance with approved allocations.

We also discussed long-term orbital debris concerns. Even small satellites are expected to behave responsibly at the end of their mission life. Nobody wants uncontrolled transmitters or partially active systems remaining indefinitely.

The satellite should essentially “clean up after itself” when operations are finished.

***Engineering review comments:***

- *Radio parameters (transmission frequency within licensed allocations, transmit power level, beacon interval, and data rate) must be configurable via commanding.*
- *Passive atmospheric drag acceptable as deorbit approach in LEO.*
- *End-of-life behavior includes transmitter shutdown and battery passivation.*

## Memo D — Ground Operations Workshop

Operators cannot babysit the spacecraft continuously. Ground station passes are short and sometimes missed entirely.

We need regular status information so we know whether the spacecraft is alive. Even something small every few hours would help enormously.

If the spacecraft skips reporting to conserve energy, we still want to understand why. Otherwise, troubleshooting becomes guesswork.

Command capability is also essential. Commands must not be accepted blindly — mistakes happen, and unauthorized transmissions are a real concern. We want some form of authentication and a record of what was sent.

Software updates are expected during the mission. Universities always discover improvements after launch. However, if an update breaks the spacecraft, it must recover automatically.

***Engineering review comments:***

- *Assume ~2–4 ground passes/day, ~5–10 minutes each.*
- *Assume the spacecraft periodically transmits a short health beacon (on the order of every few hours) containing basic power, thermal, and operational state information. The beacon should prioritize robustness over data rate.*
- *Command authentication required.*
- *Software update recovery/fallback mechanism expected.*

## Memo E — Reliability and Safety Discussion

Spacecraft fail because small problems cascade. A temperature spike or battery issue should not immediately end the mission.

There should be a conservative configuration in which the spacecraft focuses solely on survival and communication with Earth.

Batteries are especially sensitive. Deep discharge events are one of the most common failure causes in small satellites. Protect them even if it interrupts payload activities.

Computers also crash sometimes — radiation happens. Recovery mechanisms should exist even if they are simple resets.

***Engineering review comments:***

- *Operational modes preferred over immediate shutdown on faults.*
- *Safe configuration disables payloads and high-power transmitters.*
- *Deep battery discharge causes permanent damage.*
- *Radiation resets expected → watchdog/reset recovery typical.*

## Memo F — Mechanical and Integration Coordination

Payload teams change frequently, so interfaces should not require redesign every time. Ideally, we connect payloads using a predictable electrical and mechanical interface.

Operators also asked whether payload power could be switched remotely. That would simplify troubleshooting experiments behaving unexpectedly.

***Engineering review comments:***

- *Payload interface should provide standard power rails and data link (e.g., serial/CAN-like).*
- *Payload power switching controlled by onboard computer is typical.*

## Memo G — Thermal and Power Engineering Consultation

Temperature swings in orbit are significant. Sunlight heats the spacecraft quickly, eclipse cools it rapidly. Sensors alone are not enough — something has to react when limits are approached.

Power margins are another concern. During eclipse there is no solar generation. Loads must be managed so batteries survive repeated cycling.

***Engineering review comments:***

- *Target internal operational temperature roughly −10 °C to +50 °C.*
- *Thermal reactions may include heaters or payload shutdown.*
- *Eclipse duration assumption ≈ 30–40 minutes/orbit. Targeted orbit takes 95 minutes.*
- *Power prioritization and budgeting required.*

## Memo H — Verification Planning Meeting

We are not interested in architecture diagrams that cannot be checked. Teams should think about how they would prove the system works.

Even simple verification thinking helps — tests, inspections, or analysis approaches tied to the design decisions.

Traceability between expectations and design elements should be visible.

***Engineering review comments:***

- *Verification method should be considered early (test, inspection, analysis).*
- *Requirement‑to‑architecture traceability expected.*

## Memo I — Radio Network User Meeting

Users expect the satellite to listen frequently enough to be useful. If it is asleep most of the time, the relay service loses value.

That said, radio regulators impose limits on how transmissions are used. Compliance must be demonstrable.

Messages should not disappear simply because the spacecraft cannot forward them immediately.

***Engineering review comments:***

- *Typical CubeSat UHF receivers consume about 1–2 W when active, comparable to baseline avionics power consumption. Continuous listening is therefore uncommon; assuming a 10–50 % receiver duty cycle is reasonable, depending on available energy (about 9–10 minutes of listening per 95-minute orbit at 25 %).*
- *Incoming traffic may arrive opportunistically whenever the satellite is listening, typically at 9.6–19.2 kbps using short burst transmissions. Individual user messages or telemetry packets commonly range from a few hundred bytes to several kilobytes, and multiple users may transmit during the same orbital pass.*
- *Ground communication opportunities are limited; assuming approximately three ground station passes per day with 5–10 minutes of usable link time per pass is reasonable. At 19.2 kbps with roughly 70 % effective throughput, total daily downlink capacity may reach only a few megabytes.*
- *Weather or operational issues may prevent successful downlink for up to 72 hours. Persistent onboard storage should therefore be sized to accommodate multiple days of accumulated traffic, including operational logs.*

