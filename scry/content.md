# Building a Proof of Concept: Distributed Internet Monitoring

## The Challenge
A global organization needed to quantify problematic internet at remote locations. They wanted BigQuery + PowerBI integration, but organizational momentum was lacking until there was a working proof of concept.

## My Approach: Spike Solution
I built a rapid prototype using existing open-source components, focusing on **decision-making over perfection**.

### Key Decisions Made

**1. Leverage Existing Work**
- Started with Geerling's internet-pi project (90% of what we needed)
- Focused on the missing 10%: distributed data collection and automated updates

**2. Skip PowerBI Integration**
- Early scope decision: PowerBI interface was outside efficient development scope
- Chose Looker Studio for visualization (faster to implement)

**3. Use Personal Google Account**
- Organization lacked access/approval for BigQuery
- Built proof of concept with personal account to demonstrate value

**4. Optimize for Data Volume**
- Initial version: 10,000 records per night (unusable)
- Solution: Single record per device every 5 minutes with unique device IDs

## Technical Challenges & Quick Wins

**DNS Breaking on Install**
- Problem: Playbook broke DNS resolution
- Solution: Check for systemd-resolved symlink before modifying resolv.conf
- **Decision**: Fix the immediate blocker, not redesign the system

**Container Health Checks**
- Problem: Services marked unhealthy despite running
- Solution: Adjusted health check parameters
- **Decision**: Make it work, not perfect

**Credential Management**
- Problem: Complex setup process
- Solution: Interactive script with secure defaults
- **Decision**: Good enough for PoC, improve later

## Results
- **Working prototype** in 2 weeks
- **Data flowing** to BigQuery from multiple locations
- **Visualization** in Looker Studio
- **Automated updates** via systemd service

## Lessons for Rapid Prototyping

**1. Scope Aggressively**
- PowerBI integration would have taken me weeks to learn
- Looker Studio took hours
- **Decision**: Prove value first, polish later

**2. Use What Works**
- Geerling's project handled 90% of requirements
- Focused on the unique 10% (distributed collection)
- **Decision**: Don't rebuild, extend

**3. Accept Technical Debt**
- GitHub Actions for CI/CD (unsuitable for production, but terrific for getting rapid feedback)
- Personal Google account for BigQuery
- **Decision**: Get it working, production concerns come later

**4. Get something working early**
- 10,000 overnight records → lead to implementing 1 record per device per 5 minutes
- Discover issues fast!

## Impact
The proof of concept demonstrated:
- **Feasibility** of distributed monitoring
- **Value** of centralized data collection
- **Need** for organizational support

## Next Steps
- Simplify installation process
- Move to organizational Google account
- Production-ready CI/CD pipeline

## Key Takeaway
**Proof of concepts should prove visible value, not perfection.** Focus on the critical path, accept technical debt, and optimize for demonstration over production readiness.

## Resources
- GitHub repository link
- Documentation
- Community contributions
- Related projects and tools
https://github.com/roguisharcanetrickster/internet-pi
https://github.com/roguisharcanetrickster/custom-metrics
