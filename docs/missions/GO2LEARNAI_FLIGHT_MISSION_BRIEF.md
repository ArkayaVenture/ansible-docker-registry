# GO2LEARNAI AUTONOMOUS FLIGHT MISSION

## Mission

During this execution window, operate a coordinated autonomous engineering team to advance Go2LearnAI across:

1. Cloudflare / India access
2. SCORM interoperability
3. SCORM sample content
4. Jev AI evaluation + POC
5. Hermes Agent evaluation + POC
6. Slack Agent application
7. Go2LearnAI <-> Slack integration
8. Soul-Verse + Google/cloud cost optimisation
9. Shared memory / second-brain improvement
10. Token, model and infrastructure cost optimisation

The objective is **working artefacts and evidence**, not research notes alone.

---

# 0. GLOBAL OPERATING RULES

## Orchestration model

Use:

**MISSION ORCHESTRATOR**
↓
specialist workstreams
↓
independent verifier
↓
integration agent
↓
release/readiness report

Do not run as an uncontrolled flat swarm.

The Mission Orchestrator owns:

- task dependency graph
- priorities
- budget
- shared architecture decisions
- blocking questions
- agent assignments
- final integration
- acceptance criteria
- evidence
- status dashboard

Agents must exchange:

- task state
- repository paths
- decisions
- APIs/contracts
- test results
- evidence
- blockers

Do NOT exchange huge conversation histories.

---

# 1. FLIGHT COMMAND-CENTRE CHECKLIST

## P0 - start immediately

☐ Discover Go2LearnAI repositories, deployment environments and documentation

☐ Identify production / staging / development environments

☐ Create a shared mission board:
- TODO
- RUNNING
- BLOCKED
- REVIEW
- DONE

☐ Capture current architecture

☐ Capture current Cloudflare setup

☐ Capture current Google/cloud estate

☐ Capture Soul-Verse infrastructure and subscriptions

☐ Identify current authentication/SSO architecture

☐ Identify Slack workspace and existing apps/integrations

☐ Establish cost baseline

☐ Establish agent/token budget

---

## P1 - run in parallel

☐ Fix Cloudflare access from India

☐ Create safe Go2LearnAI dummy/test account for Abhinav

☐ Research and architect SCORM support

☐ Build first SCORM package

☐ Investigate Jev AI

☐ Build Jev POC

☐ Investigate Hermes Agent

☐ Build Hermes POC

☐ Design Slack App

☐ Implement Slack App skeleton

☐ Build Go2LearnAI <-> Slack identity mapping

☐ Build Go2LearnAI <-> Slack course interaction

☐ Audit Soul-Verse costs

☐ Audit Google/cloud costs

---

## P2 - integrate

☐ Import SCORM package into Go2LearnAI

☐ Track SCORM completion/progress/score

☐ Expose course functionality through Slack

☐ Test learner identity mapping

☐ Test course enrolment lookup

☐ Test learning content delivery

☐ Test progress retrieval

☐ Test notifications

☐ Test assessment result flow

☐ Compare Jev vs Hermes roles

☐ Decide which capabilities belong in Go2LearnAI

☐ Produce cost-remediation plan

---

## P3 - verification

☐ Security review

☐ RBAC review

☐ PII review

☐ token/cost review

☐ architecture review

☐ automated tests

☐ integration tests

☐ regression tests

☐ rollback plan

☐ update second brain

☐ produce final mission report

---

# WORKSTREAM A - CLOUDFLARE / INDIA ACCESS

## Mission

Determine why Go2LearnAI login/access from India is failing and restore legitimate access without weakening the global security posture.

## Agent tasks

A1. Discover:
- Cloudflare zone
- DNS
- WAF
- Access
- Zero Trust
- geo rules
- IP rules
- bot protection
- rate limiting
- authentication callbacks
- country restrictions
- identity provider configuration

A2. Reproduce using:
- staging environment where possible
- browser automation
- India-region test environment
- controlled VPN/cloud test endpoint where authorised

A3. Determine whether failure occurs at:

DNS → Cloudflare edge → WAF → Cloudflare Access → application → IdP → callback → application session

A4. Make the smallest safe correction.

DO NOT simply disable geo protection globally.

## Abhinav test account

Create a dedicated TEST identity rather than sharing an administrator/user's real credentials.

Required characteristics:

- non-production privileges
- no billing permission
- no admin permission
- least-privilege learner/test role
- identifiable as test account
- easy to revoke
- audit logging enabled

Credentials must be transferred using an approved secure secret-sharing method.

Never place passwords/API keys in:
- Slack channel
- Git
- documentation
- long-term agent memory
- prompts

External sharing or permission changes require human approval.

## Definition of Done

- India access reproduced
- root cause documented
- safe fix implemented/tested
- test account works
- UK access regression tested
- security posture unchanged or improved
- rollback documented

---

# WORKSTREAM B - SCORM ARCHITECTURE

## Mission

Determine the correct role of SCORM within Go2LearnAI.

## Research

Evaluate:

### SCORM 1.2
Needed because many organisations still have existing SCORM packages.

### SCORM 2004
Support:
- manifest
- SCO launch
- completion
- success
- score
- suspend/resume
- sequencing where appropriate

### Also evaluate

- xAPI
- cmi5
- LTI 1.3 / LTI Advantage
- Common Cartridge where relevant

## Architectural principle

Go2LearnAI must NOT become internally dependent on SCORM.

Create:

SCORM Adapter
→ Go2LearnAI Learning Event API
→ canonical internal learning model

For example:

SCORM completion
→ learning.completed

SCORM score
→ assessment.score

SCORM bookmark
→ learner.resume_state

SCORM status
→ enrolment.progress

This allows future xAPI/cmi5/LTI integrations to use the same internal model.

## Required outputs

- standards comparison
- compatibility matrix
- Go2LearnAI recommendation
- architecture diagram
- SCORM import workflow
- SCORM player/runtime approach
- data model
- threat/security review
- test strategy

---

# WORKSTREAM C - SCORM CONTENT POC

Build an actual small SCORM course.

## Course

Title:

**Introduction to Responsible AI Agents**

Target duration:
10-15 minutes

Structure:

1. What is an autonomous agent?
2. Agent vs chatbot
3. Tools and permissions
4. Memory
5. Human approval
6. Safety
7. Mini assessment

## Package should demonstrate

- launch
- learner identity
- lesson status
- completion
- score
- bookmark/resume
- final assessment
- pass/fail where applicable

Create:

1. SCORM 1.2 version
2. SCORM 2004 version if practical

Output:

/scorm-poc/
    README.md
    scorm-1.2/
    scorm-2004/
    source/
    tests/
    screenshots/

The package must be validated using an independent SCORM testing environment where authorised.

---

# WORKSTREAM D - JEV AI POC

## Mission

Evaluate whether Jev can act as a typed decision layer inside Go2LearnAI.

Do NOT treat Jev as another general chatbot.

Candidate use cases:

### Course recommendation decision

INPUT:

learner profile
course history
role
skills
course catalogue

OUTPUT:

{
  recommended_course_ids,
  confidence,
  reason_codes,
  requires_human_review
}

### Learner risk decision

INPUT:

progress
assessment attempts
inactivity
engagement

OUTPUT:

{
  risk_level,
  intervention,
  confidence
}

### AI action approval

INPUT:

requested agent action
user permissions
organisation policy
risk

OUTPUT:

{
  allow,
  deny,
  require_approval
}

## POC requirement

Implement ONE narrow typed decision use case.

Measure:

- latency
- reliability
- cost
- type safety
- explainability
- integration complexity
- fallback behaviour

## Stop condition

If "JEV" discovered in the target environment is not Jev AI / jev-ai, do not silently substitute.

Record the ambiguity and return it to the orchestrator.

---

# WORKSTREAM E - HERMES AGENT POC

## Mission

Evaluate Hermes Agent as an autonomous execution/runtime component for Go2LearnAI.

Investigate:

- skill mechanism
- persistent memory
- tool execution
- MCP support
- API server
- model routing
- session management
- self-learning behaviour
- Slack capability
- cost controls
- sandboxing
- permission boundaries

## POC

Run Hermes as a separate service.

Architecture:

Go2LearnAI
→ Agent Gateway
→ Hermes
→ approved tools
→ Go2LearnAI APIs

Do NOT allow direct unrestricted database access.

Initial Hermes task:

"Given learner ID X, retrieve their authorised training context and suggest the next appropriate learning action."

Expected result:

structured JSON + trace.

## Comparison

Compare:

Hermes
vs
Claude Code
vs
existing agent infrastructure

across:

- autonomy
- coding
- operational execution
- memory
- skills
- tool use
- browser use
- integration
- cost
- security
- observability

Do not replace an existing component unless there is measurable benefit.

---

# WORKSTREAM F - SLACK AGENT APPLICATION

## Mission

Make Slack a first-class Go2LearnAI learning surface.

Initial user experience:

User opens Slack and can:

- ask Go2LearnAI questions
- discover courses
- receive recommendations
- start learning
- continue previous learning
- query progress
- ask questions about course material
- receive reminders
- view upcoming learning
- submit simple responses
- get links back into Go2LearnAI

## Core commands/interactions

Examples:

"show my courses"

"continue my AI course"

"what training do I need?"

"show my progress"

"explain this module"

"quiz me"

"recommend something for Kubernetes"

## Architecture

Slack User
↓
Slack App
↓
Identity Broker
↓
Go2LearnAI API Gateway
↓
Learning APIs
↓
Agent Gateway
↓
specialist agents

## Identity

Map:

Slack workspace
+
Slack user ID

to

Go2LearnAI tenant
+
Go2LearnAI learner identity

Never rely solely on email matching after initial linking.

Implement:

- OAuth
- tenant binding
- user linking
- revocation
- token rotation
- permissions
- audit trail

## Security

Start read-only wherever possible.

Write actions such as:

- enrol learner
- submit assessment
- modify course
- administer tenant

need separate explicit permissions.

---

# WORKSTREAM G - END-TO-END SLACK/LMS INTEGRATION

Required proof:

### Flow 1 - Identity

Slack user
→ Go2LearnAI user resolved

### Flow 2 - My Learning

Slack
→ "Show my courses"
→ authorised courses returned

### Flow 3 - Continue Learning

Slack
→ "Continue"
→ correct course/module selected
→ secure deep link issued

### Flow 4 - Ask course question

Slack
→ user question
→ retrieve relevant course content
→ answer grounded in course material

### Flow 5 - Progress

Slack
→ Go2LearnAI progress API
→ formatted response

### Flow 6 - Agent recommendation

Slack
→ recommendation agent
→ authorised recommendation
→ explain reason

### Flow 7 - Notification

Go2LearnAI event
→ event bus
→ Slack notification

Examples:

course assigned
deadline approaching
course completed
assessment feedback available

---

# WORKSTREAM H - SOUL-VERSE + GOOGLE/CLOUD COST REDUCTION

## Mission

Find why infrastructure and licence costs are growing and implement safe savings.

Do not start by deleting resources.

## Collect

For at least the previous 30-90 days:

- service
- resource
- environment
- owner
- region
- utilisation
- cost
- cost trend
- licence count
- active-user count
- idle time
- storage
- egress
- LLM/token cost
- database cost
- observability cost

## Categorise

### KEEP

required and appropriately sized

### RIGHTSIZE

oversized CPU/RAM/database/GPU

### SCHEDULE

non-production resources capable of shutdown outside working hours

### CONSOLIDATE

duplicate services/databases/tooling

### CACHE

repeat calls/data that should be cached

### ROUTE CHEAPER

workload does not need premium LLM/model

### REMOVE

confirmed unused resources

### LICENCE OPTIMISE

paid users with insufficient use

## Specific AI cost analysis

Measure:

cost per:
- learner
- course
- generated lesson
- agent task
- 1,000 requests
- successful autonomous task

Track:

input tokens
output tokens
cached tokens
tool calls
retries
model
agent
task
tenant

---

# TOKEN OPTIMISATION POLICY

Agents must not automatically send the entire project memory to every model request.

Use progressive context retrieval.

## M0

ephemeral scratchpad

Do not persist.

## M1

current run state

Persist only until task completion/checkpoint.

## M2

execution episodes

Persist:
- what was attempted
- outcome
- error
- fix
- evidence

## M3

Go2LearnAI durable project knowledge

Persist:
- architecture decisions
- APIs
- deployment decisions
- stable conventions
- product requirements

## M4

validated procedures/skills

Examples:

"how to deploy Slack integration"

"how to produce Go2LearnAI SCORM package"

"how to diagnose Cloudflare login"

A procedure only becomes M4 after successful execution/test.

## M8

live observations

Examples:

current:
- Cloudflare rules
- billing
- GitHub state
- current APIs
- current deployment

Apply TTL.

---

# SECOND-BRAIN WRITE POLICY

At the end of every substantial task create:

### TASK OUTCOME

What changed?

### DECISION

What was decided?

### EVIDENCE

What proves this?

### ARTEFACTS

URLs/repositories/files/commits.

### FAILURE/LESSON

What failed and why?

### NEXT ACTION

What should the next agent do?

### MEMORY ROUTE

M2 / M3 / M4 / M8.

Do not persist:
- passwords
- access tokens
- secrets
- transient debugging output
- full raw chat transcripts unless required

---

# MODEL ROUTING POLICY

Use the cheapest capable model.

### Small/fast model

Use for:
- classification
- extraction
- formatting
- routine tests
- summarisation
- log filtering

### Strong coding model / Claude Code

Use for:
- repository architecture
- implementation
- debugging
- refactoring
- integration tests

### High-reasoning model

Use only for:
- architecture conflicts
- security analysis
- complex design
- difficult debugging
- final synthesis

### Local model

Prefer for:
- repetitive processing
- classification
- internal summarisation
- non-sensitive batch tasks where quality is sufficient

---

# CONTEXT EFFICIENCY

Never send:

whole repository
+
whole second brain
+
whole conversation
+
all logs

to a model automatically.

Instead:

task
→ retrieve relevant memory
→ retrieve relevant code
→ retrieve relevant evidence
→ execute

Use code search / AST / embeddings / graph retrieval to locate context before reading files.

Create shared artefacts once and reference them by ID/path rather than repeatedly reproducing them.

---

# AUTONOMOUS ACCESS POLICY

Agents should attempt capabilities in this order:

1. existing local tool
2. approved API
3. connected plugin
4. approved MCP connector
5. browser automation
6. request human access

If the system is accessible only through browser:

- use browser automation
- use existing authorised identity
- respect MFA
- never bypass security controls

If access is unavailable:

create an ACCESS REQUEST containing:

SYSTEM:
REQUIRED ROLE:
WHY REQUIRED:
MINIMUM PERMISSION:
TASK BLOCKED:
EXPECTED DURATION:

Then continue all non-blocked work.

Agents must never invent credentials.

---

# HUMAN APPROVAL GATES

Agents may autonomously research, code, test and create pull requests.

Require approval before:

- production deployment
- destructive cloud change
- resource deletion
- permission escalation
- external communication
- sharing credentials
- creating production users
- changing billing commitments
- purchasing licences
- exposing a new public endpoint
- materially weakening a security policy

---

# SHARED AGENT OUTPUT FORMAT

Every specialist returns:

STATUS:
DONE / PARTIAL / BLOCKED

SUMMARY:

CHANGES:

ARTEFACTS:

TESTS:

COST IMPACT:

SECURITY IMPACT:

MEMORY WRITES:

UNRESOLVED:

RECOMMENDED NEXT STEP:

CONFIDENCE:

---

# FINAL MISSION DELIVERABLE

The Orchestrator must produce one final:

## GO2LEARNAI FLIGHT MISSION REPORT

including:

### Executive summary

### Completed
- Cloudflare
- SCORM
- Jev
- Hermes
- Slack
- Cost optimisation

### Architecture decisions

### Working POCs

### Pull requests / commits

### Screenshots / test evidence

### Cost baseline

### Identified savings

### Security findings

### Memory additions

### Token usage

### Agent/model cost

### Blockers requiring ST

### Recommended next 7 days

### Go / No-Go recommendations

No workstream can be marked DONE merely because research was completed.

DONE requires either:

working implementation,
validated artefact,
measured analysis,
or documented decision with evidence.