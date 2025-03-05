# GitHub Issue Templates Guide

This repository contains standardized issue templates for use across all organization projects. These templates are designed to streamline our development workflow, maintain consistency, and improve productivity for both technical and product teams.

## Table of Contents

- [GitHub Issue Templates Guide](#github-issue-templates-guide)
  - [Table of Contents](#table-of-contents)
  - [Available Templates](#available-templates)
  - [Template Locations](#template-locations)
  - [Estimation Guidelines](#estimation-guidelines)
    - [T-Shirt Sizing](#t-shirt-sizing)
    - [Story Point Estimation](#story-point-estimation)
    - [Time-Based Estimation](#time-based-estimation)
    - [Calculating Team Velocity](#calculating-team-velocity)
    - [Sprint Capacity Planning](#sprint-capacity-planning)
  - [Template Usage Guide](#template-usage-guide)
    - [For Product Managers](#for-product-managers)
      - [User Stories](#user-stories)
      - [Sprint Planning](#sprint-planning)
    - [For Technical Team Members](#for-technical-team-members)
      - [Development Tasks](#development-tasks)
      - [Bug Reports](#bug-reports)
    - [For Scrum Masters / Team Leads](#for-scrum-masters--team-leads)
      - [Retrospectives](#retrospectives)
  - [Best Practices](#best-practices)
    - [Linking and References](#linking-and-references)
    - [Labels and Projects](#labels-and-projects)
    - [Definition of Done (DoD)](#definition-of-done-dod)
    - [Template Customization](#template-customization)
  - [Need Help?](#need-help)

## Available Templates

Our templates are designed to support the full scrum process:

1. **User Story** - Product-focused features with business value and acceptance criteria
2. **Bug Report** - Detailed bug reports with severity and sprint impact assessment
3. **Development Task** - Technical implementation tasks with clear definition of done
4. **Sprint Planning** - Template for planning sprint goals and capacity
5. **Retrospective** - Structured format for sprint retrospectives

## Template Locations

These templates are stored in the organization-wide `.github` repository in:

```
.github/
├── ISSUE_TEMPLATE/
│   ├── user_story.yml
│   ├── bug_report.yml
│   ├── development_task.yml
│   ├── sprint_planning.yml
│   ├── retrospective.yml
│   └── config.yml
├── ISSUE_TEMPLATE_DOCS/
│   └── README.md
└── profile/
    └── README.md
```

## Estimation Guidelines

Consistent estimation is critical for predictable delivery. We use multiple complementary approaches:

### T-Shirt Sizing

T-shirt sizing provides a quick relative size estimate for user stories.

| Size | Description | Story Points | Typical Timeline | Examples |
|------|-------------|--------------|------------------|----------|
| XS | Very small, well-understood work | 1-2 | < 1 day | Simple text change, Minor UI tweak |
| S | Small, straightforward work | 3-5 | 1-2 days | Form field addition, Simple API endpoint |
| M | Medium complexity | 8 | 3-5 days | New feature with 2-3 components, Database schema change |
| L | Large, complex work | 13 | 1-2 weeks | Complex feature with multiple components, Integration with external system |
| XL | Very large work | 21+ | 2+ weeks | **Should be broken down further** |

**Important**: Any story sized as L or XL should be considered for breaking down into smaller stories.

### Story Point Estimation

Story points represent the relative effort, complexity, and uncertainty of work.

**Fibonacci Sequence**: We use the Fibonacci sequence (1, 2, 3, 5, 8, 13, 21) for story point values to reflect the increasing uncertainty with larger estimates.

**Factors to Consider When Estimating**:
- Technical complexity
- Unfamiliarity with the domain
- Dependencies on other systems
- Testing requirements
- Documentation needs
- Code review overhead

**Estimation Process**:
1. Team reviews the user story and asks clarifying questions
2. Team members privately assign points (Planning Poker)
3. Reveal estimates and discuss outliers
4. Reach consensus on final estimate

### Time-Based Estimation

For development tasks, we use hour-based estimates to help with daily planning.

| Estimate | Description | When to Use |
|----------|-------------|-------------|
| 1h | Very quick task | Simple code changes, review tasks |
| 2h | Small task | Bug fixes, minor enhancements |
| 4h | Half-day task | Component implementation, moderate refactoring |
| 1d (8h) | Full-day task | Complex component, feature integration |
| 2d (16h) | Two-day task | Maximum size for a single task |
| 3d+ | Too large | Break down into smaller tasks |

**Rule of Thumb**: If a task is estimated at more than 2 days (16 hours), it must be broken down further.

### Calculating Team Velocity

Velocity measures how many story points a team completes in a sprint.

**Calculation Method**:
1. Sum the story points of all completed stories in a sprint
2. Track velocity over multiple sprints
3. Use the average of the last 3 sprints for future planning

**Example**:
- Sprint 1: 25 points
- Sprint 2: 32 points  
- Sprint 3: 28 points
- Average Velocity: 28.3 points

**Velocity Considerations**:
- New team members might temporarily decrease velocity
- Team improvements should gradually increase velocity
- Consistent sprint lengths are essential for meaningful velocity tracking

### Sprint Capacity Planning

When planning sprints, follow these steps:

1. **Calculate Raw Capacity**:
   - Team members × Working days × Hours per day = Raw capacity in hours
   - Example: 5 developers × 10 days × 6 productive hours = 300 hours

2. **Apply Reduction Factors**:
   - Meetings: -10% (standups, planning, etc.)
   - Context switching: -10%
   - Unexpected work: -10%
   - Final capacity: Raw capacity × 0.7
   - Example: 300 hours × 0.7 = 210 productive hours

3. **Convert to Story Points**:
   - Use historical data to establish hours-per-point ratio
   - Example: If 1 point historically takes 4 hours, then 210 hours ÷ 4 = 52.5 points theoretical capacity
   - Plan conservatively at 80-90% of theoretical capacity
   - Example: 52.5 points × 0.85 = ~45 points planned for sprint

## Template Usage Guide

### For Product Managers

#### User Stories

1. Use the User Story template when defining new features
2. Complete all required fields, focusing on:
   - Clear title following "As a [user], I want to [action] so that [benefit]" format
   - Business value that ties to strategic objectives
   - Detailed acceptance criteria that define "done"
   - T-shirt size estimation for sprint planning

#### Sprint Planning

1. Create a Sprint Planning issue at the start of each sprint
2. Link all user stories committed for the sprint
3. Define 1-3 clear sprint goals
4. Document team capacity and velocity metrics
5. Identify potential risks and blockers

### For Technical Team Members

#### Development Tasks

1. Create development tasks from user stories during sprint planning
2. Always link to the parent user story
3. Break down work into tasks no larger than 2 days of effort
4. Complete implementation details with specific technical requirements
5. Use the Definition of Done checklist to ensure quality standards

#### Bug Reports

1. Use the Bug Report template for any defects
2. Set appropriate severity level
3. Document reproduction steps clearly
4. Assess sprint impact to help with prioritization
5. Add technical context to assist developers

### For Scrum Masters / Team Leads

#### Retrospectives

1. Create a Retrospective issue at the end of each sprint
2. Document sprint metrics (planned vs. completed)
3. Facilitate team discussion on what went well and areas for improvement
4. Document specific action items with assignees
5. Reference the retrospective in the next sprint planning

## Best Practices

### Linking and References

- Always use the `#` reference syntax to link related issues (#123)
- Maintain the hierarchy: Tasks link to Stories, Stories link to Epics
- Reference issues in commit messages using the `Fixes #123` or `Relates to #123` syntax

### Labels and Projects

- Use consistent labels to enable filtering and reporting
- Add issues to the appropriate project board
- Use GitHub's automation features to move cards through columns

### Definition of Done (DoD)

Before closing any issue, ensure it meets these criteria:

**For User Stories**:
- All acceptance criteria passed
- All tasks completed
- Feature tested by at least one other team member
- Documentation updated
- Product owner approval obtained

**For Development Tasks**:
- Code implemented according to requirements
- Unit tests written and passing
- Code reviewed and approved by at least one team member
- Integration tests passing
- No new technical debt introduced (or documented if unavoidable)

**For Bug Fixes**:
- Root cause identified and documented
- Fix implemented and verified in development environment
- Regression tests added where applicable
- Original reporter verified the fix (when possible)

### Template Customization

If you need to customize these templates for a specific repository:

1. Copy the templates from `.github/ISSUE_TEMPLATE/` to your repository's `.github/ISSUE_TEMPLATE/` directory
2. Modify as needed for project-specific requirements
3. Custom templates in a repository will override these organization-wide templates

## Need Help?

- For questions about these templates, contact @ramanaditya
- For process questions, reach out to your Scrum Master
- For suggestions, create an issue in this repository using the Bug Report template