# Session 07 Reflection
## Why Lists Beat Variables at Scale

Manual auditing doesn't scale. If an analyst checked 100 servers for 
open ports by hand — one IP at a time — they would spend hours on a 
task a script can finish in seconds. That's the core argument for 
automation, and it's what Session 07 made concrete.

Using a single List to store IP targets, combined with a for loop, 
means the socket connection logic — specifically `s.connect_ex((ip, 
port))` — is written once and executed against every target 
automatically. Writing 100 separate variables would mean writing that 
logic 100 times, multiplying the surface area for errors and making 
the code impossible to maintain.

Two details from today's lab are worth holding onto:

**Data types matter.** IPs are Strings. Ports are Integers. Python 
treats them differently and the socket library requires them in the 
right form. Passing a port as a string will break the connection 
silently.

**`settimeout` is not optional in production.** Without it, a dead 
host will hang the entire script indefinitely. Setting 
`s.settimeout(1)` caps the wait at one second per target — the 
difference between a tool that finishes and one that stalls.

The bigger takeaway: a for loop isn't just a convenience. It's the 
difference between a script that checks 5 IPs and one that checks 
5,000 without changing a single line of logic.

## References

The Knowledge House. (2026). *T1-M3-S07: The Automation Forge —
Python Fundamentals for Security.* TKH Innovation Fellowship 
Cybersecurity Program, Phase 1.
