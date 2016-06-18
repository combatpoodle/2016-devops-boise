# 2016-devops-boise notes



# Jit Kumar
sp?

Intro Gary Gruver - works with execs of large trad orgs to implement agile/devops

# Gary Gruver - starting and scaling devops


# Grady ?, alertsense

## Software arch to support CD

UML'd it :'(

LEAN, AGILE, DEVOPS, CD -> delops

### Arch provides:
* incremental change
* commit test with easy to use frameworks
* release benign changes
  * Feature flagging
* automated db migrations
  * evolutionary db design, schema management, etc
* commit pipeline for CD changes

### CI/CD pipeline design

Commit early/often

### Architectural/VC continuum
Video by laurie voss (npm) - monolith vs microservice - evolve to scalable

### To arch/microservices
Migration to microservices as APIs are defined and used to isolate

### takeaways
Start with modular monolith
Feature flag

# Eugene Dina - engineering manager at Bodybuilding

## Why decops?
* Deployments are slow
* Resource Contention
* Large monoliths

## How did we accomplish it?
* Empower devs (with root access)
* Responsibility for what happens (good ideas end up winning)
* No one to call when something goes wrong
* Forces testing and quality to be a priority
* Deployments happen as necessary
* Automate everything
* Monitor everything

## Challenges
* Separation of duties
* ownership/oversight on critical components - you have to account for X, Y, Z - tools are up to devs
  * MFA, strict with a small group and opens up as needed
* Infrastructure design
  * VPCs, subnets, IAM rules
* Consider your resources

## Benefits
* Short dev cycles, frequent/small deployments
* Smaller technical issues
* Roll forwards/back easily
* Reduction of bottlenecks
* Devs are empowered and encouraged to experiment
* Leads to employee satisfaction

## Tools
* Jenkins
* slack
* puppet
* github
* terraform
* datadog
* pagerduty
* packer
* consul

## Automation
* lots of small deployments
  * 2287 last year
* environment consistency
* ability to scale quickly via config/autoscaling
* 100 servers same as 1
* Have a tagging strategy

## Monitoring
## CMS Implementation
* 40k articles
* 500k assets
* 30M visitors/month
* team of 3 engineers
* 3 months

## Demo
Free network topology map for all!  (Ok, just staging)

# Greg Lonnon, continuous agile consultant, arch at thuron

## Jenkins 2.0 IAC
Demo on bitbucket somewhere - bitbucket/boise_devops_2016

Cloudbees released pipeline stage view
Back-compat with 1.6
BlueOcean UI - material design
Maturing job DSL and pipeline
REST UI (?)

Job DSL is new, developed/supported by netflix, written in groovy

### Pipeline
Groovy/DSL based
Developed by cloudbees
Modern-ish

### Best practice

* CI/CD using IAC
* CI/CD as releasable component
* Pipeline/jenkinsfiles as future; ad hoc pipeline jobs

# Scentsy - Matt Eagy and Chris Johnson

Application of CD at Scentsy

120k consultants
1000 employees
24M orders in 5 years

Needs rapid integration of new ideas

### Custom SW platforms:
* Business tools for consultants, marketing material, etc
* Ecommerce platform for consultants to sell with
* Corporate Back Office
* 3rd party integrations

Scentsy 5.0 core MVC/API

### Why CD
Culture/business reqs -> technical challenges -> adverse business business impact

### business objectives
Stability
Lredictability
Quality
Safety/fast failure
Validate customer value
Business Alignment
Scalability/predictability/quality

### Measurable Goals
* 75% boost in deoy freq
* decrease cycle time 33%
* 50% defect decrease
* 70% increase in on task work

### CD theory/understanding
High rate of controlled change through rapid and reliable delivery
Build/measure/learn cycle

It's about organization/architecture/process

### constraints
* dates
* multiple teams/applications
* tightly coupled apps
* db deployments
* stakeholder communication/UAT
* deployment schedules

### Team/culture
Moving to same room improved collab
Involved ops early on organically

### Deployment Systems
* Monolithic systems
  * Branching Model - releases
  * constraint is lack of automated testing
* Microservice Systems
  * deploy off master/trunk
  
### Deployment over iew
Repo->build->qa->staging->prod->dr

Microservices build on a dev's box

### Tools
M$

### Devops wins
Blue/green
DC migration
Deployment automation/orchestration
Virtualization
Automated Tests
Integration of SDLC
Monitoring dashboards

### KPIs
* Downtime dropped near 0, was originally near 1hr/deploy
* Days between deployments 30 days -> several per day
* Number of features in dev up 1/3
* Cycle time - 50 days to 40 days
* Defects down a bunch

### Recipe
Config management
Hiring mixed dev/ops backgrounds
Automation orchestration
Perf tests
Crawl/walk/run on deployments
Build trust with partners

### takeaways
* Understand why you want to change
* reserve capacity
* start with agile/scrum
* try things and revert
* get measurable fast

### People are key
* communicate
* be transparent
* continuous improvement

### q
* what was biggest challenge?
  * building a plan, not affecting prod systems, align repos, apply SOC.... Organization
* How to test usability/etc?
  * Feature flag, deploy to prod

# Macy's - Penny Garrison and Tommy Mouser

Suits largely care about bottom line

Success measured in business *and* technology metrics

Macy's passed its first billion dollar year, quarter, month, aiming for week

Penny/paul are focused on iOS/Android - 50% of traffic to their site is mobile

DevOps drives business fundamentals/goals - allows quick movement

### Why automate
* test in minutes not weeks
* cheaper medium/long term
  * requires upfront investment in vms, frameworks, automated tests
  * reduce manual resources
* keep trunk stable
* increase release cadence with more features and higher quality

### Case: iOS
#### Objective

Cadence, cycle, replace manual resources

### Considerations
* Framework (web apps vs apps); automated testing was nonexistant
* releases/sprints - continue manual cadence while adding automation
* manual resources - retool/replace - how to change minds, headless testing, etc

### Benefits/objectives overview
* 30% release cadence improvement
* 60% regression improvement
* reduce/replace manual resources; 100% automation engineers - automation people get nagged  by manual tasks
* automation on sim, manual on device

### Case study B - android (WIP)
#### Objective
* Unifying framework, teams
* Tests run on both platforms
* Deterministic tests - don't bother automating if it's not deterministic
* concurrently scale tests across devices

#### Beginning State
* 2 teams in 5 locations
* 2 frameworks
* 2 tests for same behavior
* manual device testing

#### Considerations
* start from scratch vs combining current frameworks
* latest tools and their benefits - language or solution change?
* setting common standards and practices
* device farm
  * automated testing solution influences
* mocking solution
  * tests run in both real and mocked environments to determine if failures are internal/external

#### Expected benefits
* combined tests
* maintain release cadence
* reduce resources 2:1 dev:qe
* deterministic test results
  * trust testing results
  * mocking allows determination of environment or code issues causing failures
* concurrently scale testing across multiple devices
  * test in actual hardware

# Mike Young, Agile Planning/WIP

## Why?
Managing ask, expectations, process and communicating it outwards

Throughput = k/WIP

Feature estimation activities: (non-JIT)
* drive up WIP
* Lock-in features

Controlling WIP in-flow to increase throughput

### Taming planning
* In 2008, business required final feature list 12 months in advance; estimation blocked progress for ~1 month; all estimation was a wash due to incomplete execution, design changes, etc

* Prioritize Everything - priorities self-drive organization; rank drives what feature gets help/etc
* Light-touch prediction for story sizes - t-shirt sizing
* system engineers doing jit design and light-touch sizing
* commit by delivering, not by estimating
* predict throughput based on history
* deliver smallest possible feature to field, deliver independently

### Getting mgmt/mktg buy in to agile planning
* prioritize product turn-on delivery/qualification ahead of new features
* separate new feature requests from make it work
* you get 20% more features this way because we aren't wasting effort
* externals decide together on priorities
* governors approve feature req list
* ability to work on last-minute requests


### Over-drove the WIP
* mgmt would treat non-delivered as pre-commit to next release

### Features and stories must earn their way on
* requestors have to follow through to end product now and can't force release date
* nothing on list is automatic
* single continuous train with 2-month on/off cycle
* solution test groups clean subepics for 2 months instead of 5-6 months
* dedicated teams work until a feature until it's done
* they commit at under 50%; commit to things marketing is going to stick on the box
* Feature requests require business analysis for ROI; helps prioritization and allows removal of tasks which really aren't needed/used

