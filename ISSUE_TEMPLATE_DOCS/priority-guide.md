# Priority and RICE Scoring Guide

This document provides detailed guidance on how to properly prioritize issues using the RICE scoring method.

## RICE Scoring Framework

RICE is a prioritization framework that helps quantify the impact of work items. RICE stands for:

- **Reach**: How many users will this impact?
- **Impact**: How much will it impact each user?
- **Confidence**: How confident are we in our estimates?
- **Effort**: How much time will it take to implement?

### Calculating RICE Scores

RICE Score = (Reach × Impact × Confidence) ÷ Effort

#### Reach

Estimate how many users will be affected by this feature in a specific time period (e.g., per quarter).

| Reach Level | Description | Example |
|-------------|-------------|---------|
| 1 | Very few users (<1%) | Internal admin feature |
| 2 | Small segment (1-10%) | Power user feature |
| 3 | Moderate segment (10-25%) | Feature for specific user role |
| 4 | Large segment (25-50%) | Common feature most users will see |
| 5 | Most/all users (>50%) | Core functionality all users interact with |

#### Impact

Measure how much this feature will impact each user who encounters it.

| Impact Level | Description | Example |
|--------------|-------------|---------|
| 0.25 | Minimal: Slight improvement | Minor UI enhancement |
| 0.5 | Low: Noticeable improvement | Small convenience feature |
| 1 | Medium: Significant improvement | New helpful feature |
| 2 | High: Major improvement | Addresses key user pain point |
| 3 | Massive: Game-changing | Transformative feature that redefines workflow |

#### Confidence

Estimate how confident you are in your Reach and Impact estimates.

| Confidence Level | Description | When to Use |
|------------------|-------------|------------|
| 50% | Low confidence | Limited data, new market, many assumptions |
| 70% | Medium confidence | Some data, educated guesses |
| 90% | High confidence | Solid data, strong evidence, similar to previous successful work |
| 100% | Full confidence | Absolute certainty (rarely used) |

#### Effort

Estimate the total team effort required (in person-weeks).

| Effort Level | Description | Sprint Equivalent |
|--------------|-------------|------------------|
| 0.5 | Very small | Less than half a sprint for one person |
| 1 | Small | One sprint for one person |
| 2 | Medium | One sprint for two people or two sprints for one person |
| 4 | Large | Multiple sprints or multiple people |
| 8+ | Very large | Consider breaking down the project |

### RICE Score Interpretation

Higher RICE scores indicate higher priority. Use these guidelines:

| RICE Score Range | Priority Level | Guidance |
|------------------|----------------|----------|
| <1 | Low | Consider deferring or removing from roadmap |
| 1-5 | Medium | Important but not urgent, schedule in upcoming quarters |
| 5-15 | High | Important for upcoming releases |
| >15 | Critical | Top priority, schedule in next sprint |

## Relationship Between RICE and Issue Templates

### User Story Template

In our User Story template, we've simplified this to a dropdown with four options:

- **Critical** (Must have for release) = Highest RICE scores (>15)
- **High** (Important for release) = High RICE scores (5-15)
- **Medium** (Nice to have) = Medium RICE scores (1-5)
- **Low** (Future consideration) = Low RICE scores (<1)

### Bug Report Template

For bugs, we use severity rather than RICE:

- **Blocker**: System/feature completely unusable
- **Critical**: Major functionality broken
- **Major**: Significant impact to users
- **Minor**: Limited impact, workaround exists
- **Trivial**: Cosmetic issues

## Practical Application Tips

1. **Be Consistent**: Use the same scale across all features for fair comparison
2. **Re-evaluate Regularly**: Update scores as new information becomes available
3. **Team Input**: Get multiple perspectives when scoring
4. **Document Assumptions**: Note what led to your scoring decisions
5. **Avoid Analysis Paralysis**: The framework is meant to aid decisions, not replace judgment

## Example RICE Calculation

**Feature**: Add single sign-on capability

- **Reach**: 4 (Will affect 40% of users)
- **Impact**: 2 (High impact - simplifies login process)
- **Confidence**: 90% (0.9) (Have solid user research data)
- **Effort**: 3 person-weeks

**RICE Score**: (4 × 2 × 0.9) ÷ 3 = 2.4

This would be classified as a **Medium** priority feature.