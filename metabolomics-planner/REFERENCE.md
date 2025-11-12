# Metabolomics Analysis Implementation Guide: Interactive Workflow

## Overview

This document provides a comprehensive framework for creating client-facing metabolomics implementation plans that bridge scientific best practices with laboratory capabilities. The workflow emphasizes **interactive decision-making** with clear, scannable information and numbered options to avoid overwhelming clients.

---

## Core Workflow Principles

### 1. Start with Quick Overview
- Provide scannable workflow (max 15 lines)
- Use visual indicators (✓ = have it, ⚠️ = critical gap, ℹ️ = enhancement)
- Brief mentions of key steps

### 2. Present Gaps Interactively
- Number all gaps (Gap 1, Gap 2, etc.)
- Maximum 8 lines per gap
- Clear decision format (Option 1/2, Yes/No, or numbered choices)
- Allow "APPROVE ALL" for quick decisions

### 3. Offer Next Steps Based on Response
- User can request "MORE INFO: Gap [number]"
- User can request "ALTERNATIVES: Gap [number]"
- User can type gap numbers with decisions
- User can approve all recommendations at once

---

## Process Flow

### Stage 1: Initial Request Analysis

**Inputs Required:**
- Client inquiry (any level of detail)
- Laboratory capability documentation
- Sample information (type, number, study goals)

**Analysis Steps:**
1. Parse client requirements
2. Identify analysis type (targeted, untargeted, specific metabolite classes)
3. Document existing laboratory capabilities relevant to request

---

### Stage 2: Literature Research Phase

**Research Strategy:**
- Search peer-reviewed literature (2014-present preferred)
- Focus on validated LC-MS/MS methods for specific metabolite class
- Prioritize clinical and metabolomics laboratory publications
- Look for FDA/regulatory-compliant methods when applicable

**Key Research Areas:**
- **Chromatography:** Column types, mobile phases, gradient conditions
- **Sample Preparation:** Extraction methods, cleanup procedures
- **Internal Standards:** Requirements for quantitative analysis
- **MS Parameters:** Ionization modes, detection methods (MRM, etc.)
- **Validation:** Acceptance criteria, performance metrics
- **Throughput:** Expected runtime, sample capacity

**What to Extract:**
- Recommended equipment/consumables
- Expected performance metrics (accuracy, precision, sensitivity)
- Typical timelines for method development
- Common pitfalls or challenges
- Cost ranges when available

**Citation Strategy:**
- Brief, specific references embedded in recommendations
- Focus on "what" and "why" over excessive detail
- Cite to justify: equipment purchases, methodology choices, validation criteria

---

### Stage 3: Gap Analysis Framework

**For Each Analysis Component:**

1. **Assess Current Laboratory Capability**
   - What equipment/methods do we have?
   - Is it functional and validated?
   - Staff trained and competent?

2. **Compare to Literature Best Practices**
   - What do top laboratories use?
   - What's considered the "gold standard"?
   - Are there newer/better approaches?

3. **Identify and Categorize Gaps**
   - ✓ **Already Optimal:** Acknowledge and build on strengths
   - ⚠️ **Critical Gap:** Must address, explain why
   - ℹ️ **Enhancement:** Nice-to-have, not essential

4. **For Each Gap, Provide:**
   - Specific product/method recommendation
   - Cost estimate and lead time
   - Scientific justification (with citations)
   - Impact on timeline if not addressed
   - Clear decision options

**Gap Categories:**

| Category | Symbol | Examples | Action |
|----------|--------|----------|--------|
| Critical | ⚠️ | Missing ISTD, wrong column | Must address |
| Enhancement | ℹ️ | Automation, alternative methods | Optional |
| Satisfied | ✓ | Current equipment adequate | Acknowledge |

---

## Deliverable Format: Quick Analysis Overview

### Template Structure

```markdown
# [Analysis Type] - Analysis Overview

## Quick Analysis Path

Based on your request to **[restate user's goal]**, here's how we'll proceed:

### Recommended Workflow

**Sample Type:** [Type] ✓ (your lab can handle) OR ⚠️ (gap identified)

**Analysis Approach:** [Targeted/Untargeted] using [method] ✓

**Sample Preparation:** [Method name] ✓ OR ⚠️
- [Key step 1 - one line]
- [Key step 2 - one line]
- [Key step 3 - one line]
- **Note:** [Any important consideration]

**Chromatography:** [Column type] ✓ OR ⚠️
- [Mobile phase brief description]
- [Runtime estimate]
- **Note:** [Any optimization needed]

**Detection:** [Ionization and scan type] on Altis ✓
- [Brief parameters]
- **Note:** [Any consideration]

**Quality Control:** Full FDA-compliant QC framework ✓
- [Brief QC mention]

---

## Critical Gaps Requiring Action

### Gap 1: [Item Name] ⚠️
**Issue:** [One sentence explaining why needed]

**Solutions:**
1. [Option 1: Product name, supplier, cost, lead time]
2. [Option 2 if applicable]

**Your decision needed:** [Clear question - e.g., "Which option? (Type 1 or 2)"]

### Gap 2: [Item Name] ⚠️ OR ℹ️
**Issue:** [One sentence]

**Solution:** [Single solution or numbered options]

**Your decision needed:** [Clear format - e.g., "Approve? (Yes/No)"]

[Repeat for 3-5 gaps maximum]

---

## Summary: What You Need to Decide

**Critical purchases (~$[total], [X]-week lead time):**
- [Item 1 - cost]
- [Item 2 - cost]

**Timeline impact:**
- [Phase 1]: [duration]
- [Phase 2]: [duration]
- **Total: [X-Y weeks] to analysis-ready**

**Your immediate actions - Type your decisions:**
1. [Gap 1 decision point] ([format])
2. [Gap 2 decision point] ([format])
3. [Gap 3 decision point] ([format])

Or simply type **"APPROVE ALL"** to proceed with all recommendations.

---

## Next Steps After Your Decisions

Once you respond, I'll generate either:
- **Detailed Gap Analysis** (if you need more info: type "MORE INFO: Gap [number]")
- **Alternative Options** (type "ALTERNATIVES: Gap [number]")
- **Full Implementation Plan** (if you approve - complete 16-section plan)
```

---

## Example: Amino Acid Analysis (Interactive Format)

### Client Request
"We need to analyze amino acids in human liver tissue samples. We have 50 samples from a clinical study."

### Response: Quick Analysis Overview

```markdown
# Targeted Amino Acid Analysis - Analysis Overview

## Quick Analysis Path

Based on your request to **quantify amino acids in 50 human liver tissue samples**, here's how we'll proceed:

### Recommended Workflow

**Sample Type:** Human tissue (liver) ✓ (your lab handles all tissue types)

**Analysis Approach:** Targeted LC-MS/MS using MRM ✓
- Quantify all 20 proteinogenic amino acids
- Your Thermo Altis is ideal for this

**Sample Preparation:** 80% Methanol Extraction (Method A) ✓
- Pre-extraction ISTD addition (critical!)
- Validated in your lab for tissue
- 10 µL solvent per mg tissue
- Centrifugation, SpeedVac concentration
- **Note:** Your lab has this method validated

**Chromatography:** Specialized amino acid column ⚠️
- Intrada Amino Acid column needed (gap - see below)
- 10-13 minute separation
- **Note:** Your C18 columns won't retain polar amino acids adequately

**Detection:** Positive ESI-MRM on Altis ✓
- High sensitivity (femtomole detection)
- Monitor transitions for 20 amino acids
- **Note:** Scheduled MRM for increased sensitivity

**Quality Control:** Full FDA-compliant QC framework ✓
- Pooled tissue QC, blanks, calibrators, QC standards

---

## Critical Gaps Requiring Action

### Gap 1: Intrada Amino Acid Column ⚠️
**Issue:** C18 columns show weak retention for polar amino acids; HILIC produces broad peaks. Literature demonstrates Intrada as standard for complete amino acid separation.

**Solution:** Purchase Intrada Amino Acid column (Imtakt)
- Product: 50 × 3 mm or 150 × 3 mm, 3 µm
- Supplier: Imtakt USA or chromatography distributors
- Cost: $800-1,200
- Lead time: 1-2 weeks

**Your decision needed:** Approve purchase? (Yes/No)

### Gap 2: Stable Isotope-Labeled Internal Standards ⚠️
**Issue:** FDA guidelines require isotope-labeled ISTD for accurate quantification. Corrects for extraction efficiency, matrix effects, and instrument variability.

**Solutions:**
1. Complete 13C/15N-labeled amino acid mix (17-20 compounds) - $1,000-1,500
2. Representative ISTD set (6-8 key amino acids) - $500-800

**Your decision needed:** Which option? (Type 1 or 2)

### Gap 3: Calibration Standards ⚠️
**Issue:** Need certified amino acid reference standards for calibration curves

**Solution:** Purchase certified amino acid standard mix
- Cost: $200-400
- Lead time: 1-2 weeks

**Your decision needed:** Approve? (Yes/No)

### Gap 4: Method Development Time ℹ️
**Issue:** New column requires gradient optimization

**Solution:** 2-3 weeks method development
- Optimize gradient for best separation
- Test different mobile phase compositions
- Standard procedure, no additional cost

**Your decision needed:** Acceptable timeline? (Yes/No)

---

## Summary: What You Need to Decide

**Critical purchases (~$2,000-3,100, 2-week lead time):**
- Intrada column: $800-1,200
- ISTD mix: $500-1,500 (or $1,000-1,500 for complete set)
- Calibration standards: $200-400

**Timeline impact:**
- Standards/column procurement: 1-2 weeks
- Method development: 2-3 weeks
- Method validation: 2-4 weeks
- Sample analysis (50 samples): 1 week
- Data processing: 1-2 weeks
- **Total: 8-12 weeks from approval to results**

**Your immediate actions - Type your decisions:**
1. Gap 1 - Intrada column (Yes/No)
2. Gap 2 - ISTD option (1 or 2)
3. Gap 3 - Calibrators (Yes/No)
4. Gap 4 - Method development timeline (Yes/No)

Or simply type **"APPROVE ALL"** and select ISTD option: **"APPROVE ALL, Gap 2: Option 1"**

---

## Next Steps After Your Decisions

Once you respond, I'll generate:
- **Full Implementation Plan** (16-section detailed plan for execution)

Need more information?
- Type "MORE INFO: Gap [number]" for detailed explanation
- Type "ALTERNATIVES: Gap [number]" for different approaches
```

---

## Handling User Responses

### Response Type 1: Approve All
**User types:** "APPROVE ALL" or "APPROVE ALL, Gap 2: Option 1"

**Action:** Generate Full Implementation Plan (16 sections) immediately

---

### Response Type 2: Specific Decisions
**User types:** "Gap 1: Yes, Gap 2: Option 1, Gap 3: Yes, Gap 4: Yes"

**Action:** Generate Full Implementation Plan with approved specifications

---

### Response Type 3: Request More Information
**User types:** "MORE INFO: Gap 2"

**Action:** Provide expanded explanation of that specific gap
```markdown
## Detailed Information: Gap 2 (Stable Isotope-Labeled ISTD)

### Why ISTD Are Critical for Amino Acid Quantification

**Scientific Rationale:**
Stable isotope-labeled internal standards (ISTD) are isotopically-labeled versions of your target metabolites (e.g., 13C6-leucine). They:

1. **Correct for Extraction Efficiency:**
   - Added before extraction, they experience same losses as endogenous metabolites
   - Typical recovery: 70-90%, varies by sample
   - Without ISTD: Cannot distinguish biological variation from technical variability

2. **Correct for Matrix Effects:**
   - Serum/tissue components can suppress or enhance MS signal (±50% typical)
   - ISTD experiences same suppression/enhancement
   - Peak area ratio (analyte/ISTD) normalizes this effect

3. **Correct for Instrument Drift:**
   - MS sensitivity varies over long sequences (±10-20%)
   - ISTD tracks these changes
   - Essential for multi-day studies

**FDA Requirement:**
FDA Bioanalytical Method Validation Guidance (2018) requires that "a stable isotopically labeled internal standard should be used whenever possible" for quantitative LC-MS/MS assays.

**Option 1 vs Option 2:**

**Option 1: Complete Mix (17-20 amino acids)**
- Pros: Individual ISTD for each target, most accurate, meets FDA best practices
- Cons: Higher cost ($1,000-1,500)
- Recommended for: Publication-quality studies, clinical applications

**Option 2: Representative Set (6-8 amino acids)**
- Pros: Lower cost ($500-800), adequate for exploratory studies
- Cons: Some amino acids use surrogate ISTD (less accurate)
- Recommended for: Pilot studies, screening studies

**Suppliers:**
- Cambridge Isotope Laboratories (broad selection)
- Sigma-Aldrich (pre-mixed options)
- Toronto Research Chemicals (custom mixes)

**My Recommendation:** Option 1 if budget allows - ensures publication-quality data and regulatory compliance.

**Your decision:** Which option? (Type 1 or 2)
```

---

### Response Type 4: Request Alternatives
**User types:** "ALTERNATIVES: Gap 1"

**Action:** Provide alternative solutions
```markdown
## Alternative Solutions: Gap 1 (Chromatography Column)

### Alternative 1: Optimize Existing HILIC Column ℹ️
**Approach:** Extensive gradient optimization with your existing HILIC column
- Pros: No purchase needed, use existing equipment
- Cons: Broad peaks reported in literature, may not resolve leucine/isoleucine, 4-6 weeks optimization
- Expected Performance: 15-18 amino acids well-separated, 2-3 isomer pairs unresolved
- **Trade-off:** Saves $1,000 but sacrifices data quality and adds time

### Alternative 2: Derivatization with C18 Column ℹ️
**Approach:** Chemical derivatization (e.g., AccQ-Tag) followed by C18 separation
- Pros: Your C18 columns work well, excellent separation
- Cons: Additional sample prep step (30 min/sample), derivatization reagents needed ($500), validation more complex
- Expected Performance: All 20 amino acids separated
- **Trade-off:** No column purchase but more labor-intensive

### Alternative 3: Intrada Column (Recommended) ⚠️
**Approach:** Purchase specialized Intrada Amino Acid column
- Pros: Literature standard, 10-13 min separation, resolves all isomers, straightforward method
- Cons: $800-1,200 cost
- Expected Performance: Complete separation of all 20 amino acids including difficult pairs
- **Why Recommended:** Most efficient path to high-quality data

### Alternative 4: Send to External Lab ℹ️
**Approach:** Outsource to commercial metabolomics facility
- Pros: No capital investment, established methods
- Cons: $50-150 per sample ($2,500-7,500 for 50 samples), loss of control, longer turnaround
- **Trade-off:** Higher per-sample cost vs. internal capability development

**My Recommendation:** Alternative 3 (Intrada column) - best balance of cost, time, and data quality. The $1,000 investment enables in-house capability for future studies.

**Your decision:** Which alternative? (Type 1, 2, 3, or 4)
```

---

## Full Implementation Plan Structure (Generated After Approval)

Once user approves gaps, generate the comprehensive 16-section plan:

### Implementation Plan Sections

1. **Executive Summary** (2-3 paragraphs)
   - Project scope
   - Lab readiness (with approved gap solutions)
   - Timeline and cost summary

2. **Sample Reception & Storage**
   - Current capabilities
   - Requirements for this project

3. **Chromatography System Setup**
   - Current equipment + approved additions
   - Method parameters
   - Optimization plan

4. **Sample Preparation Workflow**
   - Detailed extraction protocol
   - QC at each step

5. **Internal Standards Strategy**
   - ISTD selected (based on user's choice)
   - Addition protocol
   - Quantification approach

6. **Mass Spectrometry Detection**
   - MS parameters
   - MRM transitions
   - Optimization strategy

7. **Quality Control Framework**
   - 5 QC sample types
   - Acceptance criteria

8. **Method Validation**
   - Parameters to validate
   - FDA guidelines compliance

9. **Sample Throughput & Batch Design**
   - Batch size
   - Randomization

10. **Data Processing & Analysis**
    - Software workflow
    - Statistical analysis

11. **Deliverables & Reporting**
    - All output files
    - Report formats

12. **Timeline & Milestones**
    - Phase-by-phase breakdown
    - Incorporating approved procurement

13. **Cost Structure**
    - One-time setup (approved items)
    - Per-sample costs

14. **Risk Assessment & Mitigation**
    - 6-8 identified risks
    - Mitigation strategies

15. **Success Criteria**
    - Method performance benchmarks
    - Validation targets

16. **Next Steps & Approval**
    - Required actions
    - Sign-off section

---

## Common Analysis Types - Quick Templates

### Targeted Metabolomics Template

**Analysis Type:** Targeted quantification of [X] metabolites

**Quick Path:**
- Sample prep: [Method A/B/D based on polarity]
- Column: [C18 for moderate polarity, HILIC for high polarity, specialized if available]
- Detection: MRM on triple quad
- Critical needs: ISTD, calibrators, method development

**Common Gaps:**
- Gap 1: Stable isotope ISTD (always critical ⚠️)
- Gap 2: Calibration standards (always critical ⚠️)
- Gap 3: Specialized column (sometimes ⚠️, sometimes ℹ️)
- Gap 4: Method validation (always required ℹ️)

---

### Lipidomics Template

**Analysis Type:** Lipid profiling/quantification

**Quick Path:**
- Sample prep: MTBE method (Method D) or Folch/Bligh-Dyer
- Column: C18 reversed-phase
- Detection: Positive & negative ESI, MRM or full scan
- Critical needs: Lipid ISTD mix, lipid calibrators

**Common Gaps:**
- Gap 1: Lipid-class ISTD mix ($1,500-3,000) ⚠️
- Gap 2: Lipid calibrators ($500-2,000) ⚠️
- Gap 3: Method development for lipid classes (3-4 weeks) ℹ️
- Gap 4: Lipid identification databases (if doing discovery) ℹ️

---

### Amino Acid Template

**Analysis Type:** Amino acid profiling

**Quick Path:**
- Sample prep: 80% methanol extraction
- Column: Intrada Amino Acid or HILIC
- Detection: Positive ESI-MRM
- Critical needs: Specialized column, amino acid ISTD

**Common Gaps:**
- Gap 1: Intrada column ($800-1,200) ⚠️
- Gap 2: 13C/15N amino acid ISTD ($500-1,500) ⚠️
- Gap 3: Amino acid calibrators ($200-400) ⚠️
- Gap 4: Method development (2-3 weeks) ℹ️

---

### Organic Acids Template

**Analysis Type:** Organic acid profiling (TCA cycle, etc.)

**Quick Path:**
- Sample prep: 80% methanol extraction
- Column: C18 or HILIC
- Detection: Negative ESI-MRM
- Critical needs: Organic acid ISTD, acidic mobile phase

**Common Gaps:**
- Gap 1: Organic acid ISTD mix ($500-1,000) ⚠️
- Gap 2: Organic acid calibrators ($300-600) ⚠️
- Gap 3: Negative ionization optimization (1 week) ℹ️
- Gap 4: Method development (2-3 weeks) ℹ️

---

## Advanced Scenarios

### Scenario 1: Multiple Gaps with Budget Constraints

**Client Response:** "Budget is tight. Can we reduce costs?"

**Your Response:**
```markdown
## Budget Optimization Options

### Current Total: $2,500 (Gaps 1-3)

**Priority Ranking:**
⚠️ **Gap 2 (ISTD) - Cannot skip:** $1,000
- Required for accurate quantification per FDA
- No workaround

⚠️ **Gap 3 (Calibrators) - Cannot skip:** $300
- Required for calibration curves
- No workaround

ℹ️ **Gap 1 (Intrada Column) - Can optimize:** $1,200
- Alternative: Use HILIC with extensive optimization (+3 weeks, saves $1,200)
- Trade-off: May not separate all isomers, broader peaks

### Budget Options:
**Option A: Full Quality ($2,500, 8-12 weeks)**
- All gaps addressed
- Best data quality
- Publication-ready

**Option B: Compromise ($1,300, 11-15 weeks)**
- Skip Gap 1 (Intrada column)
- Use existing HILIC column with optimization
- Acceptable quality for exploratory study
- May need Intrada later for publication

**Option C: Minimal ($1,300, 8-12 weeks + external column time)**
- Skip Gap 1 procurement
- Borrow/rent Intrada column from collaborator for critical samples
- Hybrid approach

**My Recommendation:** Option A if publishing results, Option B if exploratory/pilot study

**Your decision:** Which option? (Type A, B, or C)
```

---

### Scenario 2: Urgent Timeline

**Client Response:** "We need results in 4 weeks. Is it possible?"

**Your Response:**
```markdown
## Urgent Timeline Assessment

### Standard Timeline: 8-12 weeks
- Procurement: 2 weeks
- Method development: 2-3 weeks
- Validation: 2-4 weeks
- Analysis: 1 week
- Reporting: 1-2 weeks

### Fast-Track Options:

**Option 1: Expedited Procurement + Partial Validation (5-6 weeks minimum)**
- Overnight shipping for all standards (+$200)
- Concurrent method development during shipping (saves 1 week)
- Abbreviated validation (key parameters only, +risk of re-validation)
- Priority sequencing
- **Risk:** May not meet full FDA compliance, suitable for internal/exploratory only
- **Cost:** +$500 expedite fees

**Option 2: Use Existing Methods (4 weeks possible)**
- Skip Intrada column, use HILIC immediately (suboptimal separation)
- Use surrogate ISTD temporarily (less accurate quantification)
- Fast method development (1 week basic optimization)
- Limited validation (1 week)
- Analysis and reporting (2 weeks)
- **Risk:** Lower quality data, may need re-analysis for publication
- **Cost:** No additional cost, but quality compromise

**Option 3: External Laboratory (2-3 weeks)**
- Outsource to commercial metabolomics core
- Established methods, no development needed
- **Cost:** $75-150/sample = $3,750-7,500 for 50 samples
- **Trade-off:** Higher cost, loss of internal capability

**Reality Check:**
4 weeks is extremely tight for validated, publication-quality amino acid analysis with new method development. 

**My Recommendation:** 
- If truly urgent: Option 3 (external lab)
- If internal capability important: Extend to 6 weeks minimum with Option 1
- If quality cannot be compromised: Standard 8-12 week timeline

**Your decision:** Accept extended timeline (6+ weeks) or use external lab? (Type "6 weeks" or "External")
```

---

### Scenario 3: Capability Conflicts

**Client Request:** "We want untargeted metabolomics discovery"

**Lab Limitation:** Only have triple quadrupole (targeted), no high-resolution MS

**Your Response:**
```markdown
## Analysis Approach Options

### Your Request: Untargeted metabolomics (discovery)
### Lab Capability: Targeted metabolomics (triple quadrupole MS)

**Gap Identified:** Untargeted metabolomics requires high-resolution MS (Orbitrap or Q-TOF) ⚠️

### Options:

**Option 1: Acquire High-Resolution MS (long-term) ⚠️**
- Purchase Orbitrap or Q-TOF system
- Cost: $400,000-800,000
- Timeline: 6-12 months (procurement, installation, training)
- **Recommendation:** Only if ongoing untargeted work planned

**Option 2: Collaborate with Facility ℹ️**
- Partner with university/core facility with high-res MS
- Your lab: Sample prep and targeted validation
- Partner: Untargeted discovery
- Cost: $50-100/sample for discovery
- Timeline: 8-12 weeks
- **Recommendation:** Good for single project

**Option 3: Redirect to Targeted Discovery ℹ️**
- Use triple quad for "semi-targeted" approach
- Screen 200-500 metabolites using MRM library
- Less comprehensive than true untargeted
- More quantitative than untargeted
- Your lab can do this internally
- Timeline: 10-14 weeks
- **Recommendation:** Best use of your current capabilities

**Option 4: Two-Phase Approach ℹ️**
- Phase 1: External untargeted discovery (identify biomarkers)
- Phase 2: Develop targeted MRM method for candidates (your lab)
- Combined timeline: 16-20 weeks
- **Recommendation:** Best scientific approach

**My Recommendation:** Option 4 (two-phase) - leverages both discovery power and your quantitative capabilities

**Your decision:** Which option? (Type 1, 2, 3, or 4)
```

---

## Troubleshooting Common Issues

### Issue: Client Provides Minimal Information

**Client:** "I need metabolomics analysis"

**Your Response:**
```markdown
I'd be happy to help design a metabolomics analysis plan. To provide accurate recommendations, I need a few key details:

**Critical Information Needed:**

1. **Biological Question:**
   - What are you trying to discover/measure?
   - Any specific metabolites of interest?

2. **Sample Details:**
   - Sample type? (blood/plasma/serum, tissue, urine, cells, other)
   - How many samples?
   - Already collected or planning collection?
   - Current storage conditions?

3. **Analysis Goals:**
   - Discovery (find unknown metabolites) or targeted (quantify specific metabolites)?
   - Compare groups (e.g., disease vs. control)?
   - Single timepoint or longitudinal?

4. **Practical Constraints:**
   - Timeline needed?
   - Budget range?
   - Will results be published?

**Example Response Format:**
"We have 50 human plasma samples (25 diabetic, 25 control) stored at -80°C. We want to quantify glucose, lactate, and pyruvate to assess glycolytic activity. Results needed in 10 weeks for grant application."

Once you provide these details, I'll generate a customized analysis overview with specific recommendations.

**Quick Start:** If you're exploring options, I can provide a general overview for common sample types. What sample type are you working with?
```

---

### Issue: Client Rejects All Solutions

**Client:** "Too expensive / Too long / Don't want to purchase anything"

**Your Response:**
```markdown
I understand the constraints. Let me present the reality and alternatives:

## Constraint Analysis

**Cost Constraint:** Budget won't allow $2,500 in consumables
**Timeline Constraint:** Need results faster than 8-12 weeks
**No-Purchase Constraint:** Cannot acquire new equipment/standards

### What's Possible Within Constraints:

**Exploratory Analysis (Non-Validated):**
- Use existing columns (suboptimal separation)
- Use available general-purpose ISTD (less accurate quantification)
- Minimal method development (basic functionality only)
- No formal validation
- Timeline: 4-6 weeks
- Cost: No additional purchases
- **Major Limitation:** Results are qualitative/semi-quantitative only, not suitable for publication or regulatory submission

### What's Not Possible:
- ❌ Accurate quantification without proper ISTD
- ❌ FDA-compliant validation without proper standards
- ❌ Publication-quality data without optimized separation
- ❌ Meeting best practices in metabolomics field

### Alternative Paths Forward:

**Path 1: Phase the Investment**
- Month 1-2: Purchase critical ISTD only ($1,000)
- Month 3-4: Optimize with existing columns
- Month 5-6: Purchase Intrada column if needed ($1,200)
- **Benefit:** Spread costs over time

**Path 2: External Collaboration**
- Send samples to established core facility
- Pay per-sample ($50-150 each)
- No capital investment
- Established, validated methods
- **Total for 50 samples:** $2,500-7,500

**Path 3: Pilot Study First**
- Analyze 5-10 samples with existing methods (exploratory)
- Use results to justify budget for full study
- Timeline: 3-4 weeks pilot, then 8-12 weeks full study
- **Benefit:** Demonstrates feasibility before investment

**Reality Check:**
High-quality metabolomics requires investment in standards and consumables. This is true at any facility. The $2,500 we're discussing is at the low end for targeted metabolomics startup costs.

**My Recommendation:** Path 3 (pilot study) - demonstrates value before full investment

**Your decision:** Accept one of these paths or need to discuss further? (Type "Path 1", "Path 2", "Path 3", or "Discuss")
```

---

## Key Messaging Principles

### ALWAYS Include:

✓ **Lead with Strengths**
- Start with what the lab can do (use ✓ symbol)
- Build confidence in capabilities
- Acknowledge validated methods

✓ **Transparent Gap Identification**
- Use ⚠️ for critical, ℹ️ for enhancement
- One-sentence explanation of why needed
- Specific, actionable solution
- Clear cost and timeline

✓ **Numbered Decision Points**
- Every gap gets a number
- Clear response format (Option 1/2, Yes/No)
- Allow "APPROVE ALL"
- Minimize cognitive load

✓ **Realistic Timelines**
- Break into phases
- Include procurement time
- Account for validation
- Total timeline at end

✓ **Cost Transparency**
- Separate one-time vs. recurring
- Itemize all purchases
- Note volume discounts
- No hidden fees

✓ **Literature Support**
- Brief citations for key recommendations
- Support equipment choices
- Justify acceptance criteria
- Demonstrate best practices

### NEVER Include:

✗ **Over-Promising**
- Unrealistic timelines
- Guaranteed success without validation
- Performance beyond literature standards
- Capabilities you don't have

✗ **Excessive Detail in Initial Response**
- Detailed protocols
- Step-by-step procedures
- Extensive theory
- Multiple pages per gap

✗ **Overwhelming Lists**
- More than 5 gaps in initial response
- Multiple options without clear recommendation
- Bullet points exceeding 8 lines per gap

✗ **Defensive Tone**
- "As you should know..."
- Assuming client ignorance
- Over-explaining basics

✗ **Hidden Information**
- Unstated assumptions
- Unclear costs
- Vague timelines
- Buried limitations

---

## Response Length Guidelines

### Quick Analysis Overview (Initial Response)
- **Quick Analysis Path:** 10-15 lines maximum
- **Each Gap:** 5-8 lines maximum
- **Total Gaps:** 3-5 maximum in initial response
- **Summary Section:** 10-15 lines
- **Total Initial Response:** 1-2 screens (no scrolling beyond 2 screens)

### Detailed Information (When Requested)
- **"MORE INFO" Response:** 20-30 lines maximum per gap
- **"ALTERNATIVES" Response:** 4-6 options, 5-8 lines each
- Can be longer since user specifically requested details

### Full Implementation Plan (After Approval)
- **Complete 16-section document:** 20-30 pages
- Professional formatting
- Comprehensive but organized by section
- User requested full detail by approving

---

## Communication Scripts

### Initial Client Contact Response

```markdown
Thank you for your interest in [analysis type] for your study. 

To provide accurate recommendations, I'll need to:
1. Research current best practices in the literature
2. Compare with our laboratory capabilities
3. Identify any gaps or requirements

This will take approximately [15-30 minutes]. I'll then provide you with:
- Quick overview of the recommended workflow
- Any critical gaps that need addressing (with costs and timeline)
- Clear decision points so you can approve or modify the approach

Would you like me to proceed with this analysis?

**Quick Questions to Get Started:**
- Sample type: [Blood/tissue/cells/other]?
- Number of samples: [X]?
- Specific metabolites of interest (if any): [list or "comprehensive profiling"]?
- Timeline needs: [X weeks/months]?
```

---

### Presenting Initial Overview

```markdown
# [Analysis Type] - Analysis Overview

I've reviewed the literature for [analysis type] and compared it with our laboratory capabilities. Here's the quick overview:

[Insert Quick Analysis Path - 15 lines max]

[Insert Critical Gaps - 3-5 gaps, 8 lines each]

[Insert Summary - What You Need to Decide]

**Response Options:**
- Type gap numbers with your decisions (e.g., "Gap 1: Yes, Gap 2: Option 1")
- Type "APPROVE ALL" to proceed with all recommendations
- Type "MORE INFO: Gap [number]" for detailed explanation
- Type "ALTERNATIVES: Gap [number]" for different options
- Type "DISCUSS" if you'd like to talk through options

I'm here to answer questions and refine the approach based on your needs.
```

---

### After Client Approves

```markdown
Excellent! I'll now generate your comprehensive Implementation Plan with all approved specifications.

**What You've Approved:**
- [Gap 1]: [Decision]
- [Gap 2]: [Decision]
- [Gap 3]: [Decision]
- Timeline: [X-Y weeks]
- Total Investment: $[amount]

**The Implementation Plan will include:**
1. Executive Summary
2. Detailed Sample Preparation Protocol
3. Chromatography Setup & Optimization
4. MS Parameters & Method Development
5. Quality Control Framework
6. Method Validation Plan
7. Timeline with Milestones
8. Complete Cost Breakdown
9. Risk Assessment & Mitigation
10. Success Criteria
11. Deliverables & Reporting
12. Next Steps & Approval Section

Generating now... [then provide full 16-section plan]
```

---

### When Client Requests More Information

```markdown
## Detailed Information: Gap [X] - [Item Name]

[Provide 20-30 lines of detailed explanation including:]

### Scientific Rationale
[Why this is needed - reference literature]

### Technical Details
[How it works, what it does]

### Options Comparison
[If multiple options, compare in detail]

**Option 1:** [Name]
- Pros: [list]
- Cons: [list]
- Cost: $[X]
- Best for: [use case]

**Option 2:** [Name]
- Pros: [list]
- Cons: [list]
- Cost: $[X]
- Best for: [use case]

### My Recommendation
[Clear recommendation with reasoning]

### Impact If Not Addressed
[What happens if we skip this]

**Your decision:** [Clear question with format]
```

---

### When Client Requests Alternatives

```markdown
## Alternative Solutions: Gap [X] - [Item Name]

I've identified [4-6] alternative approaches:

### Alternative 1: [Name] [⚠️ or ℹ️]
**Approach:** [Brief description]
- **Pros:** [2-3 bullets]
- **Cons:** [2-3 bullets]
- **Cost:** $[X] OR saves $[Y]
- **Timeline:** [X weeks] OR adds [Y weeks]
- **Expected Performance:** [Brief description]
- **Trade-off:** [Key consideration]

### Alternative 2: [Name] [⚠️ or ℹ️]
[Same format]

### Alternative 3: [Name] [⚠️ or ℹ️]
[Same format]

### Alternative 4: [Recommended Option] [⚠️]
[Same format - highlight why this is recommended]

### Comparison Table

| Alternative | Cost | Timeline | Quality | Best For |
|-------------|------|----------|---------|----------|
| Alt 1 | $X | Y weeks | ★★★☆☆ | [use case] |
| Alt 2 | $X | Y weeks | ★★★★☆ | [use case] |
| Alt 3 | $X | Y weeks | ★★★☆☆ | [use case] |
| Alt 4* | $X | Y weeks | ★★★★★ | [use case] |

*Recommended option

**My Recommendation:** [Alternative X] because [brief reasoning]

**Your decision:** Which alternative? (Type 1, 2, 3, or 4)
```

---

## Metabolite-Specific Quick References

### Amino Acids
**Critical Requirements:**
- ⚠️ Intrada Amino Acid column OR HILIC ($800-1,200)
- ⚠️ 13C/15N-labeled amino acid ISTD mix ($500-1,500)
- ⚠️ Amino acid calibrator mix ($200-400)
- ℹ️ Method development (2-3 weeks)

**Sample Prep:** 80% methanol extraction (Method A)
**Detection:** Positive ESI-MRM
**Timeline:** 8-12 weeks
**Expected Performance:** Femtomole to picomole sensitivity, CV <15%

---

### Organic Acids
**Critical Requirements:**
- ⚠️ Organic acid ISTD mix ($500-1,000)
- ⚠️ Organic acid calibrators ($300-600)
- ℹ️ C18 or HILIC column (likely have)
- ℹ️ Negative ionization optimization (1 week)

**Sample Prep:** 80% methanol extraction (Method A)
**Detection:** Negative ESI-MRM
**Timeline:** 8-12 weeks
**Expected Performance:** Picomole sensitivity, CV <15%

---

### Ceramides/Sphingolipids
**Critical Requirements:**
- ⚠️ Ceramide ISTD mix ($1,500-3,000)
- ⚠️ Ceramide calibrators ($500-1,000)
- ℹ️ C18 column (likely have)
- ℹ️ Method development for ceramide separation (2-3 weeks)

**Sample Prep:** MTBE extraction (Method D)
**Detection:** Positive ESI-MRM
**Timeline:** 8-12 weeks
**Expected Performance:** Femtomole sensitivity, CV <15%

---

### Acylcarnitines
**Critical Requirements:**
- ⚠️ Acylcarnitine ISTD mix ($1,000-2,000)
- ⚠️ Acylcarnitine calibrators ($500-1,000)
- ℹ️ C18 column (likely have)
- ℹ️ Method development (2-3 weeks)

**Sample Prep:** 80% methanol extraction (Method A)
**Detection:** Positive ESI-MRM
**Timeline:** 8-12 weeks
**Expected Performance:** Picomole sensitivity, CV <15%

---

### Nucleotides
**Critical Requirements:**
- ⚠️ Nucleotide ISTD mix ($800-1,500)
- ⚠️ Nucleotide calibrators ($400-800)
- ⚠️ HILIC column (likely have)
- ℹ️ Method development (2-3 weeks)

**Sample Prep:** 80% methanol extraction (Method A)
**Detection:** Negative ESI-MRM (primarily)
**Timeline:** 8-12 weeks
**Expected Performance:** Picomole sensitivity, CV <15%

---

### Phospholipids
**Critical Requirements:**
- ⚠️ Phospholipid class ISTD mix ($2,000-4,000)
- ⚠️ Phospholipid calibrators ($1,000-2,000)
- ℹ️ C18 column (likely have)
- ℹ️ Positive and negative ionization (method development 3-4 weeks)

**Sample Prep:** MTBE extraction (Method D) or Folch
**Detection:** Positive & Negative ESI-MRM or full scan
**Timeline:** 10-14 weeks
**Expected Performance:** Picomole sensitivity, CV <20% (lipids more variable)

---

### Bile Acids
**Critical Requirements:**
- ⚠️ Bile acid ISTD mix ($1,000-2,000)
- ⚠️ Bile acid calibrators ($500-1,000)
- ℹ️ C18 column (likely have)
- ℹ️ Method development (2-3 weeks)

**Sample Prep:** MTBE extraction (Method D) or 80% methanol
**Detection:** Negative ESI-MRM
**Timeline:** 8-12 weeks
**Expected Performance:** Picomole sensitivity, CV <15%

---

### Neurotransmitters
**Critical Requirements:**
- ⚠️ Neurotransmitter ISTD mix ($800-1,500)
- ⚠️ Neurotransmitter calibrators ($400-800)
- ⚠️ HILIC or specialized column ($800-1,500)
- ℹ️ Method development (2-3 weeks)

**Sample Prep:** 80% methanol extraction (Method A)
**Detection:** Positive ESI-MRM
**Timeline:** 8-12 weeks
**Expected Performance:** Sub-picomole sensitivity (very sensitive compounds)

---

## Matrix-Specific Considerations

### Human Plasma/Serum
**Advantages:**
- Homogeneous matrix
- Well-characterized matrix effects
- Abundant literature methods

**Special Considerations:**
- Protein precipitation critical
- Matrix effects can be significant (±50%)
- ISTD essential for accurate quantification
- Test 6+ different serum lots for matrix effects validation

**Volume Required:** 50-200 µL typical
**Storage:** -80°C

---

### Tissue (All Types)
**Advantages:**
- High metabolite concentrations
- Your lab has extensive experience

**Special Considerations:**
- Homogenization critical (liquid N₂ or bead-based)
- Tissue weight accuracy important (±0.1 mg)
- Tissue type affects extraction efficiency
- Normalize to tissue weight or protein

**Amount Required:** 10-50 mg typical
**Storage:** -80°C

---

### Urine
**Advantages:**
- Non-invasive collection
- High metabolite concentrations

**Special Considerations:**
- Variable dilution (need creatinine normalization)
- pH varies (may need adjustment)
- Simple extraction (often just dilution)
- Minimal matrix effects

**Volume Required:** 50-200 µL typical
**Storage:** -80°C

---

### Cultured Cells
**Advantages:**
- Controlled conditions
- Minimal matrix complexity

**Special Considerations:**
- Quenching protocol critical (stop metabolism immediately)
- Extraction timing matters
- Normalize to cell count or protein
- Media background needs blank subtraction

**Amount Required:** 1-10 million cells typical
**Storage:** -80°C (as pellet or extract)

---

## Validation Parameters Quick Reference

### FDA Bioanalytical Validation Requirements

**Selectivity:**
- No interfering peaks >20% of LLOQ
- Test: Method blanks, matrix blanks

**Sensitivity (LLOQ):**
- S/N ≥5:1 or ≥10:1
- Accuracy: 80-120% of nominal
- Precision: CV ≤20%

**Accuracy:**
- 85-115% (80-120% at LLOQ)
- Test: QC standards (Low, Med, High)
- n=5 replicates minimum

**Precision:**
- Within-run: CV ≤15% (≤20% at LLOQ)
- Between-run: CV ≤15% (≤20% at LLOQ)
- Test: QC standards across 3+ batches

**Linearity:**
- R² ≥0.99
- Back-calculated accuracy: 85-115% (80-120% at LLOQ)
- Minimum 6 of 8 calibrators pass
- Test: Calibration curve with 6-8 points

**Matrix Effects:**
- Test: Post-extraction spike method
- Target: 85-115% (minimal suppression/enhancement)
- Test 6+ matrix lots
- ISTD should normalize matrix effects

**Recovery:**
- Not required to be high (50-120% acceptable)
- Must be consistent: CV <15%
- Test: Pre- vs. post-extraction spike

**Stability:**
- Freeze-thaw: 3 cycles
- Bench-top: Expected handling time
- Long-term: Storage duration
- Autosampler: 24-72 hours
- Acceptance: 85-115% of nominal

**Carry-over:**
- <20% of LLOQ in blank after ULOQ injection

---

## Quality Control Sample Details

### Pooled QC (Type A)
**Purpose:** Monitor system performance and data quality
**Preparation:** Pool aliquots from all study samples
**Frequency:** Every 10-15 samples
**Acceptance:** Peak area CV <30% for metabolites, <20% for ISTD

### Method Blank (Type B)
**Purpose:** Detect contamination
**Preparation:** Extraction solvent only, no sample
**Frequency:** 2-3 per batch
**Acceptance:** No peaks >20% of LLOQ

### Matrix Blank (Type C)
**Purpose:** Assess matrix selectivity
**Preparation:** Blank matrix (control tissue/plasma)
**Frequency:** 1-2 per batch
**Acceptance:** No interfering peaks at retention times

### Calibration Standards (Type D)
**Purpose:** Quantification standard curve
**Preparation:** Known concentrations (6-8 levels)
**Frequency:** Every batch (duplicate or triplicate)
**Acceptance:** R² ≥0.99, back-calculated accuracy 85-115%

### QC Standards (Type E)
**Purpose:** Validate accuracy and precision
**Preparation:** Independent from calibrators (Low, Med, High)
**Frequency:** Beginning, middle, end of batch (triplicate each)
**Acceptance:** Accuracy 85-115%, precision CV ≤15%

---

## Timeline Planning Guide

### Phase 1: Procurement (1-3 weeks)
**Activities:**
- Order critical consumables (columns, ISTD, standards)
- Typical lead time: 1-2 weeks
- Expedite options: Overnight shipping (+$200-500)

**Milestone:** All materials received and logged

---

### Phase 2: Method Development (2-4 weeks)
**Activities:**
- Column installation and conditioning
- Gradient optimization
- MS parameter optimization (source, collision energy, transitions)
- ISTD addition protocol testing
- Initial performance assessment

**Milestone:** Method achieves separation and sensitivity targets

---

### Phase 3: Method Validation (2-4 weeks)
**Activities:**
- Selectivity assessment
- LLOQ determination
- Accuracy and precision testing
- Linearity evaluation
- Matrix effects assessment
- Stability studies
- Documentation

**Milestone:** Method passes all FDA validation criteria

---

### Phase 4: Sample Analysis (Variable)
**Activities:**
- Batch preparation (randomization, QC positioning)
- Sample extraction
- LC-MS analysis
- Real-time QC monitoring

**Throughput:** 30-50 samples/day (with QC and calibration)
**Batch Size:** 20-50 samples typical

**Milestone:** All samples analyzed with passing QC

---

### Phase 5: Data Processing & Reporting (1-3 weeks)
**Activities:**
- Peak integration and review
- Quantification
- QC evaluation
- Statistical analysis
- Report generation
- Client review and revisions

**Milestone:** Final report delivered

---

## Cost Estimation Guide

### One-Time Setup Costs

**Consumables:**
- Specialized columns: $800-2,000 per column
- Internal standards: $500-4,000 (depends on metabolite class)
- Calibration standards: $200-2,000 (depends on number of analytes)
- Total typical range: $1,500-8,000

**Method Development:**
- Included in timeline
- Labor cost if charging: $2,000-5,000

**Validation:**
- Included in timeline
- Labor and materials: $3,000-8,000
- Required for FDA-compliant methods

---

### Per-Sample Costs

**Components:**
- Consumables (tubes, tips, vials): $5-10/sample
- Extraction solvents: $2-5/sample
- Internal standard: $3-8/sample
- LC-MS column wear: $5-10/sample
- LC-MS instrument time: $10-20/sample
- Data processing labor: $5-15/sample

**Total per-sample:** $30-70/sample typical

**Volume Discounts:**
- 50-100 samples: 10-15% discount
- >100 samples: 15-20% discount

---

### Statistical Analysis Costs

**Basic (often included):**
- t-tests, ANOVA, PCA
- Typically part of standard deliverables

**Advanced (additional fee):**
- Pathway analysis: $500-1,500
- Multivariate modeling: $1,000-3,000
- Custom analysis: $100-200/hour

---

## Risk Assessment Framework

### Common Risks & Mitigation Strategies

**Risk 1: Supplier Delays (Probability: Medium, Impact: Medium)**
- Mitigation: Order immediately upon approval
- Contingency: Identify alternative suppliers
- Timeline buffer: Add 1 week to procurement phase

**Risk 2: Method Development Challenges (Probability: Medium, Impact: Medium)**
- Mitigation: Literature review for similar methods
- Contingency: Consult with manufacturer technical support
- Timeline buffer: Add 1 week to development phase

**Risk 3: Matrix Effects Exceed 85-115% (Probability: Low-Medium, Impact: Medium)**
- Mitigation: Use isotope-labeled ISTD (normalizes matrix effects)
- Contingency: Sample dilution or additional cleanup
- Timeline impact: +1 week if significant optimization needed

**Risk 4: Poor Chromatographic Separation (Probability: Low, Impact: High)**
- Mitigation: Use literature-recommended columns
- Contingency: Test alternative columns or derivatization
- Timeline impact: +2-3 weeks if major changes needed

**Risk 5: Instrument Failure (Probability: Low, Impact: High)**
- Mitigation: Preventive maintenance, service contracts
- Contingency: Backup instrument or external lab
- Timeline impact: +1-4 weeks depending on repair time

**Risk 6: Sample Degradation (Probability: Low, Impact: High)**
- Mitigation: Proper storage (-80°C), temperature monitoring
- Contingency: Re-collection if possible
- Timeline impact: Study failure if re-collection impossible

**Risk 7: QC Failures (Probability: Low-Medium, Impact: Medium)**
- Mitigation: Robust QC framework, real-time monitoring
- Contingency: Troubleshoot and re-analyze affected samples
- Timeline impact: +1-2 weeks for re-analysis

**Risk 8: Budget Overruns (Probability: Low, Impact: Medium)**
- Mitigation: Detailed cost estimates upfront, contingency budget
- Contingency: Phase analysis, prioritize samples
- Timeline impact: May delay completion if funding gaps

---

## Success Criteria Definitions

### Method Development Success
- All target metabolites detected with S/N ≥10:1
- Chromatographic resolution ≥1.5 for critical pairs
- Peak symmetry <2.0
- Retention time precision <2% RSD
- Run time ≤20 minutes per sample

### Validation Success
- Selectivity: No interferences >20% LLOQ
- Accuracy: 85-115% for all QC levels (80-120% at LLOQ)
- Precision: CV ≤15% within- and between-run (≤20% at LLOQ)
- Linearity: R² ≥0.99, ≥6 of 8 calibrators pass
- Matrix effects: 85-115% or consistent across lots
- Stability: All stability parameters 85-115%

### Analysis Success
- ≥90% of samples analyzed successfully
- All QC acceptance criteria met
- No batch failures requiring re-analysis
- Complete data package delivered

### Client Satisfaction
- Results delivered on time
- Data quality meets or exceeds expectations
- Clear, comprehensive reporting
- Responsive communication throughout

---

## Documentation Requirements Checklist

### For Each Project

**Pre-Analysis:**
- [ ] Client request form or email
- [ ] Literature research summary
- [ ] Gap analysis
- [ ] Implementation plan (approved by client)
- [ ] Purchase orders for consumables
- [ ] Method development protocol

**During Analysis:**
- [ ] Sample receipt log
- [ ] Chain of custody
- [ ] Extraction logs
- [ ] Instrument sequence files
- [ ] Raw data files
- [ ] QC monitoring data
- [ ] Deviation reports (if any)

**Post-Analysis:**
- [ ] Calibration curve data and statistics
- [ ] QC performance summary
- [ ] Sample quantification tables
- [ ] Statistical analysis results
- [ ] Validation report (for new methods)
- [ ] Comprehensive final report
- [ ] Client approval/acceptance

---

## Appendix: Supplier Quick Reference

### Internal Standards & Calibrators
- **Cambridge Isotope Laboratories** - Broadest selection of isotope-labeled compounds
- **Sigma-Aldrich / MilliporeSigma** - Pre-mixed options, amino acids, organic acids
- **Avanti Polar Lipids** - Lipid standards (ceramides, phospholipids, sphingolipids)
- **Toronto Research Chemicals** - Custom ISTD mixes
- **Cayman Chemical** - Specialized metabolites, bile acids, eicosanoids

### LC Columns
- **Thermo Scientific** - Accucore C18, HILIC
- **Waters** - ACQUITY UPLC BEH C18, BEH Amide, BEH HILIC
- **Phenomenex** - Kinetex C18, Luna columns
- **Imtakt USA** - Intrada Amino Acid column (specialized)

### Solvents & Reagents
- **Fisher Scientific** - LC-MS grade solvents (Optima™)
- **Sigma-Aldrich / Honeywell** - LC-MS grade solvents
- **VWR** - Consumables, solvents

### LC-MS Consumables
- **Thermo Fisher Scientific** - Autosampler vials, caps, certified vials
- **Waters** - Vials for ACQUITY systems
- **Agilent** - Universal vials and accessories

---

## Frequently Asked Questions

**Q: How long does it take to get started with a new metabolite class?**
A: 8-12 weeks typically (2 weeks procurement, 2-3 weeks method development, 2-4 weeks validation, 1-2 weeks for first batch analysis)

**Q: Can we skip validation for exploratory studies?**
A: Yes, but data will be qualitative/semi-quantitative only. Not suitable for publication or regulatory submission.

**Q: What if we only have 5-10 samples?**
A: Minimum validation requirements still apply. Consider whether exploratory analysis is sufficient, or if you need fully validated method for future samples.

**Q: Can we add more metabolites later?**
A: Yes, if using same extraction and column. Add new ISTD and calibrators, optimize MS parameters, extend validation. Typically 2-4 weeks.

**Q: What if our samples are already degraded?**
A: Assess with pilot analysis. Degraded samples may still be usable for relative comparisons (not absolute quantification). Some metabolites are more stable than others.

**Q: Can we use your method for our own samples later?**
A: Yes, we can provide complete method documentation. You'll need to purchase your own standards and perform abbreviated validation in your lab.

**Q: How many QC samples do we need to provide?**
A: None needed upfront. We create pooled QC from small aliquots of your study samples during extraction.

**Q: What if results don't make biological sense?**
A: First check sample labeling/identity. Then assess QC data. We can re-analyze suspect samples or perform additional validation checks.

---

## Conclusion

This framework enables systematic translation of client metabolomics requests into clear, actionable plans through interactive decision-making. Key principles:

1. **Quick Overview First** - Scannable workflow with visual indicators (✓ ⚠️ ℹ️)
2. **Numbered, Actionable Gaps** - Maximum 5 gaps, 8 lines each, clear decision format
3. **Interactive Decision-Making** - Allow "APPROVE ALL" or specific gap responses
4. **Expandable Detail** - Provide "MORE INFO" and "ALTERNATIVES" on request
5. **Honest Assessment** - Transparent about capabilities, gaps, and realistic timelines
6. **Literature-Grounded** - All recommendations supported by best practices
7. **Client-Centric** - Minimize overwhelm, maximize clarity

Success comes from balancing scientific rigor with practical implementation, demonstrating expertise while maintaining accessibility, and building trust through transparency.