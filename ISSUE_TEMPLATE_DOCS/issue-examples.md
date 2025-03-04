# Example Issues with Best Practices

This document provides concrete examples of well-formed issues using our templates.

## Example 1: User Story

### Title: [STORY]: As a user, I want to reset my password so that I can regain access to my account

```markdown
## Business Value
Many users forget their passwords and need a self-service way to reset them. Currently, these users must contact support, which creates delays for users and additional work for our support team. This feature will reduce support tickets by an estimated 25% and improve user satisfaction.

## Priority (RICE Score)
High (Important for release)

## Acceptance Criteria
- [ ] User can request password reset from login screen
- [ ] System sends email with secure, time-limited (15 min) reset link
- [ ] User can set a new password that meets our security requirements
- [ ] User is notified of successful password change
- [ ] Old password no longer works after reset
- [ ] Failed reset attempts are logged and limited (max 5 in 1 hour)
- [ ] Reset link becomes invalid after use

## T-shirt Size Estimate
M (3-5 days)

## Technical Approach
- Will require updates to the authentication service
- Should use existing email service for sending reset emails
- Will need to store reset tokens securely in database with expiration
- Should enforce same password requirements as registration
- Should invalidate existing sessions when password changes

## UI/UX Considerations
- Design mock-up: [link to mockup]
- Should follow existing form design patterns
- Error states need clear user guidance
- Mobile-responsive design required

## Epic Link
#101 (Authentication Improvements)

## Testing Notes
- Test with various email providers
- Test link expiration behavior
- Test invalid token handling
- Verify security (prevent brute force attempts)
```

### What Makes This a Good User Story:
- Clear business value tied to metrics (25% reduction in support tickets)
- Detailed, testable acceptance criteria
- Technical considerations without over-specifying implementation
- Link to parent epic
- Appropriate size (M) with reasonable estimate
- Testing considerations identified

---

## Example 2: Bug Report

### Title: [BUG]: User session terminates unexpectedly after 30 minutes of activity

```markdown
## Severity
Major (Significant impact to users)

## Bug Description
Users are being logged out of the application after exactly 30 minutes even when they are actively using the system. This occurs across all browsers and devices. According to our specifications, user sessions should remain active for 2 hours of activity, with a 30-minute inactivity timeout.

## Steps to Reproduce
1. Log in to the application
2. Perform any actions continuously (clicks, form edits, page navigation)
3. After exactly 30 minutes, the user is redirected to the login screen
4. Check browser console for "Token expired" error

## Environment
production

## Technical Context
```
Error from browser console:
{
  "error": "token_expired",
  "error_description": "JWT expired at 2025-03-05T10:30:00Z"
}
```

JWT tokens appear to have a hard-coded 30-minute expiration instead of the 2-hour specification.

## Sprint Impact
Affects committed stories
- Blocks #145 (Extended reporting feature) which requires longer user sessions

## Suggested Fix
Check JWT token generation in auth-service/src/tokens.js - likely has a hard-coded 30-minute expiration (1800 seconds) instead of using the configurable session length from the environment settings.
```

### What Makes This a Good Bug Report:
- Clear severity assessment with justification
- Specific, reproducible steps
- Includes error message and technical details
- Identifies sprint impact
- Suggests potential fix with specific file location
- States expected vs. actual behavior

---

## Example 3: Development Task

### Title: [TASK]: Implement password reset email service

```markdown
## Parent Story/Issue
#135 (Password Reset Feature)

## Task Type
Feature Implementation

## Implementation Details
Create a service that:
1. Generates a secure, random token for password reset
2. Stores token in database with:
   - User ID
   - Token hash (not plaintext)
   - Expiration timestamp (15 minutes from creation)
   - Creation time
   - Used flag (boolean)
3. Sends email to user's registered email with:
   - Branded email template
   - Reset URL with token
   - Expiration information
   - Security notice

API endpoints needed:
- POST /api/auth/password-reset-request
  - Accepts email
  - Returns 200 OK regardless of email existence (security)
- GET /api/auth/validate-token/:token
  - Validates token exists and is not expired
  - Returns 200 OK if valid, 404 if invalid
- POST /api/auth/password-reset/:token
  - Accepts new password
  - Validates password requirements
  - Updates user's password
  - Invalidates token
  - Returns 200 OK on success

## Effort Estimate (hours)
1d (8h)

## Technical Notes
- Use bcrypt for token hashing
- Use existing email service adapter
- Avoid leaking user existence through API responses
- Add rate limiting to prevent abuse
- Use parameterized queries for all database operations
- Add appropriate logging (excluding sensitive data)

## Dependencies
- #132 (Email service enhancement) must be completed first
- Requires environment variables for reset URL base

## Definition of Done
- [x] Code follows team standards and patterns
- [x] Unit tests implemented
- [x] Code reviewed by at least one team member
- [x] Documentation updated (if needed)
- [x] Changes tested in development environment
```

### What Makes This a Good Development Task:
- Clearly linked to parent story
- Detailed implementation requirements
- API specifications with expected inputs/outputs
- Reasonable effort estimate (8 hours)
- Clear dependencies identified
- Definition of Done checklist
- Specific technical considerations

---

## Example 4: Sprint Planning

### Title: [SPRINT]: Sprint 24 - 2025-03-10 to 2025-03-24

```markdown
## Sprint Number
Sprint 24

## Sprint Duration
Mar 10 - Mar 24, 2025

## Sprint Goals
1. Complete user authentication flow (password reset, account verification)
2. Improve API response time by 20% for high-traffic endpoints
3. Release v1.2 to staging environment

## Sprint Scope
- #135 User password reset (M - 8 points)
- #136 Email verification (S - 5 points)
- #137 OAuth integration (M - 8 points)
- #140 API performance optimization (M - 8 points)
- #142 Dashboard caching (S - 5 points)
- #145 Extended reporting feature (L - 13 points)
- #123 Fix session timeout bug (S - 3 points)

## Team Capacity (story points)
50 points

## Previous Velocity
45 points

## Risks and Assumptions
- New team member onboarding may affect velocity
- OAuth integration depends on third-party API documentation
- Performance improvements require careful testing to avoid regressions

## Success Criteria
- All authentication stories completed and deployed to staging
- API response time reduced by 20% as measured by our monitoring system
- Zero regression bugs in existing functionality
- Code quality metrics maintained or improved
```

### What Makes This a Good Sprint Planning Issue:
- Clear, specific sprint goals (not vague)
- Detailed scope with story point estimates
- Team capacity and previous velocity for reference
- Identified risks and dependencies
- Measurable success criteria

---

## Example 5: Retrospective

### Title: [RETRO]: Sprint 23 Retrospective

```markdown
## Sprint Reference
#120 (Sprint 23 Planning)

## Sprint Metrics
- Planned velocity: 45 points
- Completed: 38 points (84%)
- 7/8 stories completed
- 1 production bug reported
- Average PR review time: 6 hours

## What Went Well
- New CI pipeline reduced build times by 40%
- Team collaboration on complex OAuth feature
- Daily standups were focused and efficient
- Technical documentation was updated promptly
- New team member onboarding process worked smoothly

## Areas for Improvement
- Underestimated complexity of reporting feature (#145)
- Several PRs remained in review for 1+ days
- Some acceptance criteria weren't detailed enough
- Local environment setup caused delays for new team member

## Action Items
- [ ] @ramanaditya - Create template for more detailed acceptance criteria
- [ ] @dev2 - Document approach for estimating complex data processing features
- [ ] @dev3 - Implement PR age notifications in Slack after 24 hours
- [ ] @dev4 - Improve local environment setup script and documentation
- [ ] All - Set aside 30 minutes daily for PR reviews

## Kudos and Recognition
- @dev1 for working extra hours to complete the API optimization
- @dev2 for mentoring our new team member
- @qa1 for catching a critical bug before production
```

### What Makes This a Good Retrospective:
- Clear metrics showing planned vs. actual
- Balanced view of positives and areas for improvement
- Specific, assigned action items with clear ownership
- Recognition for team contributions
- Link to the original sprint planning issue