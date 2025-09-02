# OmniGaze Value Streams

## Overview
This document maps OmniGaze's core value streams, showing how we deliver value from initial contact through ongoing customer success.

## 1. Lead-to-Cash Value Stream

### Overview
The complete journey from identifying a potential customer to collecting revenue and ensuring satisfaction.

### Process Flow

```
Lead Generation → Qualification → Discovery → Proposal → POC → Negotiation → Close → Delivery Project → Invoice → Collection → Success
```

**HubSpot Pipeline** (Managed by Sofie):
- Marketing → Sales Qualification → Discovery → Proposal → POC → Contract

**Delivery Model** (Technical Team):
- POC Stage → Delivery Project → Customer Success

### Detailed Stages

#### Stage 1: Lead Generation (Marketing)
**Objective**: Attract potential customers

**Activities**:
- Content marketing (blog, whitepapers)
- SEO/SEM campaigns
- Webinars and events
- Partner referrals
- Outbound prospecting

**Output**: Marketing Qualified Lead (MQL)
**Metrics**: Lead volume, cost per lead
**SLA**: 24-hour response time

#### Stage 2: Lead Qualification (SDR Team)
**Objective**: Identify genuine opportunities

**Activities**:
- Initial contact and discovery call
- BANT qualification (Budget, Authority, Need, Timeline)
- Technical fit assessment
- Stakeholder mapping

**Output**: Sales Qualified Lead (SQL)
**Metrics**: MQL to SQL conversion rate
**SLA**: 48-hour qualification

#### Stage 3: Discovery (Sales Team)
**Objective**: Understand customer needs deeply

**Activities**:
- Technical deep dive sessions
- Current state assessment
- Pain point identification
- Success criteria definition
- Stakeholder interviews

**Output**: Qualified Opportunity
**Metrics**: Discovery to proposal conversion
**Tools**: Teams recordings, transcript analysis
**Owner**: Sofie (Sales) with John (Technical)

#### Stage 4: Solution Design & Proposal
**Objective**: Present tailored solution

**Activities**:
- Solution architecture design
- ROI/business case development
- Proposal creation
- Pricing configuration
- Executive presentation preparation

**Output**: Formal Proposal
**Metrics**: Proposal win rate
**Timeline**: 5-7 days

#### Stage 5: POC (Proof of Concept) - Delivery Model
**Objective**: Demonstrate value with limited scope

**Activities**:
- POC SOW creation and signature
- Environment setup
- Limited discovery run
- Initial insights presentation
- Success criteria validation
- POC Report/Deliverable preparation

**Output**: POC Report with findings and recommendations
**Templates**: 
  - [POC SOW Template](../deliverables/poc-sow.md)
  - [POC Validation Framework](../deliverables/poc-validation-framework.md)
  - POC Report/Deliverable
**Metrics**: POC to contract conversion rate
**Timeline**: 4 weeks standard
**Owner**: Delivery team (John/Morten)

#### Stage 6: Negotiation & Closing
**Objective**: Reach mutual agreement

**Activities**:
- Commercial negotiation based on POC results
- Contract terms discussion
- Security review
- Legal review
- Procurement process navigation

**Output**: Signed Contract
**Metrics**: Average deal size, time to close
**Timeline**: 1-2 weeks post-POC

#### Stage 7: Delivery Project - Full Implementation
**Objective**: Complete platform deployment

**Project Phases**:
1. **Planning & Design Phase** (2-3 weeks)
   - Architecture Requirements Specification (ARS)
   - Architecture Design Document (ADD)
   - Implementation planning
   
2. **Implementation Phase** (4-6 weeks)
   - Full environment setup
   - Complete discovery engine deployment
   - Integration configuration
   - Comprehensive data collection
   
3. **Knowledge Transfer** (1 week)
   - User training and documentation
   - Administrator training
   - Process establishment
   
4. **Go-Live Support** (2 weeks)
   - Hypercare period
   - Performance tuning
   - Issue resolution

**Output**: Production platform with full documentation
**Templates**: 
  - [Delivery Project SOW](../deliverables/delivery-project-sow.md)
  - Architecture Requirements Specification (ARS)
  - Architecture Design Document (ADD)
**Metrics**: Time to value, project satisfaction, on-time delivery
**Timeline**: 9-12 weeks total (16 weeks in SOW template)
**Owner**: Delivery team with Customer Success handoff

#### Stage 8: Billing & Collection
**Objective**: Secure revenue

**Activities**:
- Invoice generation
- Payment processing
- Subscription activation
- Renewal scheduling

**Output**: Revenue recognition
**Metrics**: DSO (Days Sales Outstanding)
**Timeline**: Net 30 terms

#### Stage 9: Customer Success & Expansion
**Objective**: Maximize customer value

**Activities**:
- Regular success reviews
- Usage monitoring
- Expansion opportunities identification
- Renewal preparation
- Advocacy development

**Output**: Renewed/expanded contract
**Metrics**: Net Revenue Retention, NPS

## 2. Customer Success Value Stream (Cradle to Grave)

### Overview
Complete customer lifecycle management from initial contact through renewal or departure, ensuring continuous value delivery and maximizing retention. This "cradle to grave" approach ensures no customer is ever abandoned after implementation.

### Process Flow

```
Cradle: Lead Generation → Sale → Implementation
    ↓
Life: Adoption → Optimization → Expansion → Advocacy
    ↓
Grave: Renewal OR Offboarding → Lessons Learned
```

### Resource Allocation
- **John Web**: Day-to-day customer success activities
- **Partners**: Routine check-ins and support
- **John F.**: Technical escalations only
- **Morten**: Strategic customer relationships only (2-3 key accounts)

### Key Stages

#### Stage 1: Onboarding (Weeks 1-4)
**Owner**: John Web transitioning from POC
- Welcome and orientation
- Technical implementation handoff
- Initial discovery run
- Basic training completion
- First value milestone
- **Critical**: Establish Customer Success Manager relationship

#### Stage 2: Adoption (Months 2-3)
**Owner**: Customer Success Manager (John Web or Partner)
- Advanced feature training
- Use case expansion
- Process integration
- Team enablement
- Success metrics establishment
- **Stickiness Focus**: Integrate into mission-critical processes

#### Stage 3: Value Realization (Months 4-12)
**Owner**: Customer Success Manager
- Optimization recommendations
- Best practice sharing
- Expansion planning
- ROI documentation (compare to consultant costs)
- Executive business reviews
- **Key Metric**: Document savings vs. McKinsey/KPMG alternatives

#### Stage 4: Expansion & Advocacy (Year 2+)
**Owner**: Account Team with CSM
- Additional module adoption
- New use case development
- Strategic partnership evolution
- Reference and advocacy programs
- Multi-year planning
- **Target**: 145% Net Revenue Retention

#### Stage 5: Renewal or Transition
**Owner**: CSM with Sales support

**Renewal Path** (Target: 95%+):
- Value documentation
- Contract negotiation
- Success story development
- Expansion opportunities

**Departure Path** (Exception handling):
- Exit interview
- Knowledge transfer
- Lessons learned
- Win-back strategy

### Customer Success Infrastructure

#### Success Metrics
- **Adoption Rate**: Feature usage tracking
- **Time to Value**: Days to first business impact
- **Health Score**: Composite engagement metric
- **NPS**: Regular satisfaction surveys
- **Stickiness Index**: Mission-critical integration level

#### Proactive Engagement Model
```yaml
Touch Points:
  Week 1: Welcome call
  Week 4: First value check
  Month 2: Adoption review
  Month 3: Success planning
  Quarterly: Business reviews
  Annually: Strategic planning
```

#### Partner-Enabled Success
- **Training Materials**: Created by John Web
- **Playbooks**: Standardized engagement
- **Escalation Matrix**: Clear handoff points
- **Certification**: Partner CSM program

## 3. Product Development Value Stream

### Overview
From idea to deployed feature.

### Process Flow

```
Idea → Research → Design → Development → Testing → Release → Monitor → Iterate
```

### Development Stages

#### Discovery & Planning
- Customer feedback analysis
- Market research
- Technical feasibility
- Business case development
- Roadmap prioritization

#### Design & Development
- UX/UI design
- Technical architecture
- Sprint planning
- Agile development
- Code review

#### Quality & Release
- Automated testing
- Security review
- Performance optimization
- Documentation
- Staged rollout

#### Post-Release
- Usage monitoring
- Performance tracking
- Customer feedback
- Bug fixes
- Continuous improvement

## 4. Support Value Stream

### Overview
Resolving customer issues efficiently.

### Process Flow

```
Issue Reported → Triage → Diagnosis → Resolution → Verification → Documentation
```

### Support Levels

#### Level 1: First Response
- Ticket acknowledgment
- Initial triage
- Known issue resolution
- Basic troubleshooting
- Escalation decision

#### Level 2: Technical Support
- Advanced troubleshooting
- Configuration assistance
- Integration support
- Workaround provision
- Bug identification

#### Level 3: Engineering
- Code-level investigation
- Bug fixes
- Performance optimization
- Architecture consultation
- Custom solutions

## 5. Partner Value Stream

### Overview
Creating value through partnerships.

### Process Flow

```
Partner Recruitment → Enablement → Joint Planning → Co-selling → Delivery → Revenue Share
```

### Partner Types

#### Technology Partners
- Integration development
- Joint solution creation
- Technical certification
- Marketplace listing
- Co-innovation

#### Channel Partners
- Sales enablement
- Deal registration
- Joint marketing
- Commission structure
- Territory planning

#### Service Partners
- Implementation services
- Customer training
- Ongoing support
- Consulting services
- Managed services

## Value Stream Metrics

### Efficiency Metrics
- **Cycle Time**: Time through each value stream
- **Throughput**: Volume processed per period
- **Quality**: First-time success rate
- **Cost**: Cost per value stream transaction

### Effectiveness Metrics
- **Customer Satisfaction**: NPS, CSAT scores
- **Business Impact**: Revenue per stream
- **Strategic Alignment**: Contribution to goals
- **Innovation**: New value creation rate

## Cross-Stream Dependencies

### Data Flow
- Customer data flows from Lead-to-Cash to Success
- Product telemetry informs Development
- Support tickets influence Product roadmap
- Success metrics drive Sales positioning

### Process Integration
- Sales hands off to Implementation
- Support escalates to Development
- Success identifies Expansion opportunities
- Partners integrate across all streams

## Optimization Opportunities

### Automation Targets
- Lead scoring and routing
- Proposal generation
- Onboarding workflows
- Support ticket classification
- Renewal processing

### AI Enhancement Areas
- Predictive lead scoring
- Intelligent support routing
- Automated documentation
- Churn prediction
- Expansion opportunity identification

## Value Stream Management

### Governance
- Stream owners defined
- Regular performance reviews
- Cross-stream coordination
- Continuous improvement process
- Customer feedback integration

### Tools & Systems
- **CRM**: HubSpot (maintained by Sofie)
- **Development**: Atlassian suite (Jira, Confluence, Bitbucket)
- **Source Control**: Git/GitHub for strategic documentation
- **Support ticketing**: To be determined
- **Analytics**: To be determined
- **Communication**: Teams (customer meetings), evaluating Slack (internal)

---

*Last Updated: August 20, 2025*
*Next Review: Monthly value stream review*