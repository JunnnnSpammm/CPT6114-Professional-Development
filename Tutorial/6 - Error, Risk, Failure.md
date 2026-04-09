# TUTORIAL 6

## Answer the following question

1.	What are design and development factors which contribute to system errors and failures? 

- Modern systems are so interconnected that a failure in a minor sub-module can trigger a "cascading failure" across the entire network.
- If a dashboard is cluttered or confusing, users may input wrong data or miss critical warnings (e.g., the "Three Mile Island" effect).
- Failing to test for "edge cases"—unusual but possible scenarios—leads to crashes when the system encounters unexpected real-world conditions.
- Code that lacks error handling or "graceful degradation" will simply crash rather than switching to a restricted, safer mode when something goes wrong.

2.	What are management and user problems which contribute to system errors and failures?

- Unrealistic Scheduling: Management pressure to meet deadlines often leads to "cutting corners" in the QA and security auditing phases.
- Users who don't understand the system’s logic are more likely to bypass safety protocols or enter incorrect data.
- When a system usually works well, users stop paying attention, making them slow to react when an actual emergency occurs.
- Silos between the developers who build the system and the managers who deploy it can lead to a "mismatch" between what the system can do and what it is expected to do.

3.	In what ways are we safer due to new technologies?

- Cloud computing and distributed systems ensure that if one server dies, another takes over instantly without data loss.
- Robots and AI can perform dangerous physical tasks (like handling toxic waste) or repetitive monitoring tasks that would fatigue a human.
- IoT sensors can detect structural cracks in bridges or anomalies in power grids long before a human inspector could.
- We can now "test" a system in a virtual environment to see how it fails before we ever build it in the real world.

4.	To increase reliability and safety, we must use professional techniques. What are the two principles of high reliability organisations? Describe how these principles can be used to improve software and computer systems.

- **Preoccupation with Failure:** Instead of celebrating success, HROs treat any "near miss" as a symptom of a potential systemic weakness.
- **Application to Software:** Developers should use Chaos Engineering, where they intentionally "break" parts of the system to see how it responds, ensuring that small bugs don't hide larger architectural flaws.

B. Reluctance to Simplify
HROs resist the urge to give simple explanations for complex problems. They look deep into the "root cause."

Application to Computer Systems: Instead of blaming "user error," developers should analyze whether the system’s logic or UI nudged the user toward that mistake. This leads to more robust, intuitive software design.

5.	Computer system developers and other professionals responsible for planning and choosing systems must assess risks carefully and honestly. List out these assessments or safety measures. 

- Identifying potential sources of danger within the system before development begins.
- Calculating the probability of a failure and the severity of its consequences.
- Ensuring there is no "single point of failure"—if one component breaks, there is a backup.
- Having a third party (not the original developers) test the system to ensure it meets safety requirements.
- Confirming that if the system does fail, it defaults to a state that causes no harm.

## Case Study 1 [In-class discussion]
Read the article titled “Microsoft outages caused by CrowdStrike software glitch paralyze airlines, other businesses. Here's what to know” 

> https://www.cbsnews.com/news/microsoft-internet-outages-reported-worldwide/

Search the Internet to get more answers to the following questions.

1.	What had happened?

On July 19, 2024, millions of Microsoft Windows computers worldwide began crashing simultaneously, displaying the "Blue Screen of Death" 
(BSOD) and entering an endless reboot loop.

This was not a virus or a hack. It was triggered by a routine "Rapid Response Content" update sent by CrowdStrike, a leading cybersecurity 
firm, to its Falcon sensor software. Because the Falcon sensor is designed to protect the very core of the operating system, the faulty 
update caused the entire Windows system to fail immediately upon booting.

2.	What was the root cause of the incident?

The technical failure originated from a "parameter mismatch" in a configuration file (specifically Channel File 291).

* **The Logic Error:** The update contained a file that told the Falcon sensor how to inspect "named pipes" (a way processes communicate in Windows). The file instructed the sensor to look for a piece of data that wasn't there. 
* **Kernel Access:** Because the Falcon sensor operates at the Kernel level—the most privileged layer of an operating system—an unhandled error there is fatal. Instead of just the app crashing, the entire computer shuts down to prevent data corruption.
* **The Testing Gap:** The update bypassed traditional deployment "rings" (gradual rollouts). Due to a bug in CrowdStrike’s own internal validation tool, the faulty file passed through quality assurance checks without being flagged as broken.

3.	Who was/were affected and what was/were the impact from the incident? 

| Sector | Impact |
| :--- | :--- |
| **Aviation** | Over **36,000 flights delayed** and 10,000 cancelled. Major airlines (Delta, United, American) were grounded; some staff had to use hand-written boarding passes. |
| **Healthcare** | Hospitals were forced to cancel non-emergency surgeries as digital patient records and scheduling systems became inaccessible. |
| **Finance** | Banks and stock exchanges worldwide faced disruptions; ATMs went dark and digital payment systems failed in several countries. |
| **Retail/Media** | Supermarket checkouts stopped working, and major broadcasters like Sky News were unable to go on air for hours. |

4.	Suggest two ways as to how can this incident be prevented in the future.

Companies should move away from "global" instant updates. Security vendors must implement canary deployments, where an update is sent to 
only 1% of users first. Businesses should use "sandboxing"—testing updates in a restricted, non-critical environment before allowing them to 
install on every computer in the company.

Enhancing "Cyber Resilience" and redundancy. The outage highlighted the danger of a digital "monoculture" where everyone uses the same 
software. Organizations should develop manual workaround protocols*(e.g., paper-based systems) so they can function during a total IT 
blackout. Critical infrastructure should avoid relying on a single provider for all security needs, ensuring that a glitch in one tool 
doesn't bring down the entire network.
