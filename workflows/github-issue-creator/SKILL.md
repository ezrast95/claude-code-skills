---
name: github-issue-creator
description: Interactive GitHub issue creation following structured format standards with brainstorming, validation, and automated creation. Use when creating GitHub issues, filing bugs, documenting features, or when user mentions create issue, new issue, GitHub issue, or issue builder.
version: 1.2.0
dependencies:
  - GitHub CLI (gh command)
allowed-tools:
  - Read
  - Write
  - Bash
  - AskUserQuestion
---

# GitHub Issue Creator

Automate the creation of well-structured GitHub issues following established format standards through an interactive 4-phase workflow.

## When to Use

This skill activates when:
- User asks to create a GitHub issue
- User mentions "new issue", "file issue", "create issue"
- User wants to document a feature or bug
- User says "issue builder" or "GitHub issue creator"
- Planning new services, managers, or orchestrators that need tracking

## Instructions

This skill guides users through a 4-phase workflow to create professional, well-structured GitHub issues.

### Phase 1: Discovery & Brainstorming

**First, detect smart defaults:**

1. **Detect current repository**:
   ```bash
   # Get current repository from git remote or gh CLI
   gh repo view --json nameWithOwner -q .nameWithOwner 2>/dev/null || echo "amielsaa/match_table_package"
   ```
   Store as default repository.

2. **Detect available milestones**:
   ```bash
   # Get list of open milestones from the repository
   gh api repos/{owner}/{repo}/milestones --jq '.[].title'
   ```
   Identify the "current" milestone (typically the earliest open milestone or most recently created).

3. **Detect project and iterations**:
   ```bash
   # Get organization/user projects
   gh project list --owner {owner} --format json

   # For match_table_package project, get iteration field options
   gh project field-list {project_number} --owner {owner} --format json | jq '.[] | select(.name=="Iteration")'
   ```
   Default project: "match_table_package" project (detect project number)
   Get available iteration values from the project's Iteration field.

**Then ask the user these questions:**

1. **Repository Selection**:
   - Which GitHub repository should this issue be created in?
   - Default: {detected_repository} (e.g., "amielsaa/match_table_package")
   - Allow user to specify different repository if needed

2. **Milestone Selection**:
   - Which milestone/version should this issue be assigned to?
   - Default: {current_milestone} (e.g., "v1.0.0 - Initial Release")
   - Show available milestones from the selected repository
   - Allow user to accept default or choose different milestone

3. **Project Iteration Selection**:
   - Which iteration/sprint should this issue be added to?
   - Default project: "match_table_package" project
   - Show available iterations from the project (e.g., "Iteration 1", "Iteration 2", "Current Sprint")
   - This determines which kanban column the issue appears in
   - **REQUIRED**: All issues must be added to a project iteration

4. **Component Type**:
   - Is this a: service | manager | orchestrator | integration | bug | feature | documentation | other?

5. **Brief Description**:
   - What does this component/feature do? (1-2 sentences)

6. **Main Responsibilities** (bullet points):
   - What are the key responsibilities or features?

7. **Dependencies**:
   - What other components does this depend on?
   - Provide GitHub issue numbers if available (e.g., #99, #145)

8. **Priority Level**:
   - HIGH | MEDIUM | LOW

9. **File Location**:
   - Where will this code live? (full path)

10. **Additional Context**:
   - Any architectural patterns to follow?
   - Integration points?
   - Special requirements?

**Store all responses for use in Phase 2.**

### Phase 2: Structuring

Based on the component type, apply the appropriate template structure:

#### For Data Services:

```markdown
**Purpose:** {purpose from user input}

**Priority**: {HIGH | MEDIUM | LOW}

**Dependencies:**
- {Dependency 1 with issue link if available}
- {Dependency 2 with issue link if available}

**File Location:** `{file_path}`

**Integration Pattern:**
```python
class {ComponentName}:
    """
    {Brief description}
    """

    def __init__(self, database_service):
        self.database_service = database_service
        {other service initializations based on dependencies}

    def {main_method_name}(self, {parameters}) -> {ReturnType}:
        """
        {Method description}

        Args:
            {param}: {description}

        Returns:
            {return description}
        """
        # Implementation delegated to service
        pass
```

**Required Service Methods:**
{List 3-7 key methods based on responsibilities}
- `method_name(params) -> ReturnType`: Description

**Database Integration:**
{Explain which database services/tables will be used}

**Service Responsibilities:**
{List main responsibilities from user input}

**Implementation Checklist:**
- [ ] **Service Class**: Create {ComponentName} with proper initialization
- [ ] **Database Integration**: Connect to required database services
- [ ] **Core Methods**: Implement all required methods
- [ ] **Data Models**: Define/use appropriate data models
- [ ] **Error Handling**: Comprehensive error management
- [ ] **Testing**: Unit and integration tests
- [ ] **Documentation**: Complete docstrings and examples

**Testing Plan:**
1. **Unit Tests**:
   - Test each method with mocked dependencies
   - Test error conditions
   - Test edge cases

2. **Integration Tests**:
   - Test with real database connections
   - Test with actual data
   - Test performance with large datasets

**Performance Considerations:**
- Efficient database queries
- Appropriate caching strategies
- Resource cleanup

**Files to Create:**
- `{file_path}`
- `tests/{test_file_path}`

**Acceptance Criteria:**
- [ ] All methods implemented and working
- [ ] Comprehensive test coverage
- [ ] Error handling graceful
- [ ] Documentation complete
- [ ] Performance meets requirements
```

#### For Managers:

```markdown
**Purpose:** {purpose - emphasize coordination role}

**Priority**: {HIGH | MEDIUM | LOW}

**Dependencies:**
{List services this manager coordinates}
- {Service 1 with issue link}
- {Service 2 with issue link}

**File Location:** `{file_path}`

**Architectural Role:**
The {ManagerName} coordinates {domain} services following service-oriented architecture:
- **Service Management**: Initialize and coordinate all {domain} services
- **Service Coordination**: Delegate requests to appropriate services
- **Thin Delegation Layer**: Manager coordinates, services implement business logic
- **Status Aggregation**: Aggregate health and status from all services

**Integration Pattern:**
```python
class {ManagerName}:
    """
    Manages {domain} services with thin delegation pattern.

    This manager provides a unified interface for {orchestrator/caller} to access
    all {domain} functionality without directly interacting with individual services.

    Follows service-oriented architecture: manager coordinates, services implement logic.
    """

    def __init__(self, database_service):
        # Initialize services
        self.service1 = Service1(database_service)
        self.service2 = Service2(database_service)
        {additional services}

        # Shared resources
        self.database_service = database_service
        self._cache = {}  # Simple cache for frequently accessed data
```

**Required Manager Methods:**

**Service Delegation Methods (Thin Delegation):**
{List delegation methods}
- `method_name(params) -> ReturnType`: Delegate to {service_name} service

**Utility and Aggregation Methods:**
- `get_manager_status() -> Dict[str, Any]`: Aggregate status from all services
- `refresh_data_cache() -> bool`: Coordinate cache refresh across services

**Manager Responsibilities:**

**Service Coordination (Primary Role):**
- Initialize all {domain} services with proper database connections
- Provide unified interface routing requests to appropriate services
- Coordinate service lifecycle and cleanup
- **NO business logic** - all logic delegated to services

**Thin Delegation Layer:**
- Route requests to appropriate services
- Aggregate status and health information from services
- Minimal manager overhead - just coordination

**Error Handling:**
- Catch and wrap service-level errors
- Provide meaningful error messages for debugging
- Ensure partial failures are handled gracefully

**Implementation Checklist:**
- [ ] **Manager Class**: Create {ManagerName} with thin delegation pattern
- [ ] **Service Initialization**: Initialize all services
- [ ] **Delegation Methods**: Implement thin delegation methods
- [ ] **Utility Methods**: Implement status aggregation and cache management
- [ ] **Error Handling**: Wrap service errors with meaningful messages
- [ ] **Testing**: Unit tests with mocked services
- [ ] **Documentation**: Clear docstrings explaining delegation pattern

**Testing Plan:**
1. **Unit Tests (with Mocked Services)**:
   - Test service initialization and configuration
   - Test delegation to each service (verify correct service called)
   - Test error handling when services fail
   - Test status aggregation

2. **Integration Tests (with Real Services)**:
   - Test complete workflows
   - Test service coordination in realistic scenarios

**Architectural Benefits:**
- **Separation of Concerns**: Manager coordinates, services implement logic
- **Scalability**: Easy to add new services
- **Maintainability**: Manager stays thin and focused
- **Testability**: Manager tested with mocked services, services tested independently

**Files to Create:**
- `{file_path}`
- `tests/{test_file_path}`

**Related Issues:**
{List dependencies and relationships}

**Acceptance Criteria:**
- [ ] Complete {ManagerName} with thin delegation pattern
- [ ] All services initialized correctly
- [ ] All delegation methods implemented (thin delegation only)
- [ ] Status aggregation working
- [ ] Comprehensive unit tests with mocked services
- [ ] Integration tests with real services
- [ ] Manager contains NO business logic (only coordination)
- [ ] Documentation complete
```

#### For Orchestrators:

```markdown
**Purpose:** {purpose - emphasize coordination of managers}

**Priority**: {HIGH | MEDIUM | LOW}

**Dependencies:**
{List managers this orchestrator coordinates}
- {Manager 1 with issue link}
- {Manager 2 with issue link}

**File Location:** `{file_path}`

**Architectural Pattern:**
The {OrchestratorName} coordinates {number} manager subsystems:

1. **{Manager1Name}** (manages {domain}):
   {List services under this manager}

2. **{Manager2Name}** (manages {domain}):
   {List services under this manager}

**Integration Pattern:**
```python
class {OrchestratorName}:
    """
    Orchestrates all {domain} functionality.

    Follows the established orchestrator pattern:
    - {OtherOrchestrator1} coordinates {domain}
    - {OtherOrchestrator2} coordinates {domain}
    - {OrchestratorName} coordinates {number} manager subsystems

    The orchestrator does NOT directly interact with services - it coordinates
    through managers, with each manager responsible for its service domain.
    """

    def __init__(self, database_service):
        # Manager coordination - orchestrator interacts with managers, not services
        self.manager1 = Manager1(database_service)
        self.manager2 = Manager2(database_service)
        {additional managers}

        # Shared resources
        self.database_service = database_service
```

**Required Orchestrator Methods:**

**Manager Delegation Methods:**
{List methods delegating to managers}
- `method_name(params) -> ReturnType`: Delegate to {manager_name}

**Orchestrator-Level Utility Methods:**
- `get_data_summary() -> Dict[str, Any]`: Aggregate statistics from all managers
- `validate_system_health() -> Dict[str, Any]`: System health check across all managers

**Orchestrator Responsibilities:**

**Manager Coordination:**
- Initialize and coordinate manager subsystems
- Route requests to appropriate managers
- Handle cross-manager interactions and data flow
- Provide unified error reporting and logging across all managers

**Cross-Manager Data Flow:**
- Orchestrate data flow between managers when needed
- Handle dependencies between manager operations
- Ensure data consistency across all manager subsystems

**API Unification:**
- Provide single entry point for all {domain} functionality
- Standardize response formats across all manager domains
- Route requests to appropriate managers

**Implementation Checklist:**
- [ ] **Orchestrator Class**: Create {OrchestratorName} with manager integrations
- [ ] **Manager Initialization**: Initialize all managers
- [ ] **Delegation Methods**: Implement delegation to appropriate managers
- [ ] **Cross-Manager Coordination**: Handle cross-manager interactions
- [ ] **Error Handling**: Comprehensive error management across all managers
- [ ] **System Health**: Add health monitoring aggregating from all managers
- [ ] **Testing**: Unit and integration tests

**Testing Plan:**
1. **Unit Tests**:
   - Test manager initialization and integration
   - Test delegation to correct managers
   - Test cross-manager coordination logic
   - Test error handling across manager boundaries

2. **Integration Tests**:
   - Test complete workflows spanning multiple managers
   - Test cross-manager data consistency
   - Test system health monitoring

**Performance Considerations:**
- Minimal orchestration overhead (simple delegation)
- Efficient cross-manager coordination
- Proper resource management and cleanup

**Files to Create:**
- `{file_path}`
- `tests/{test_file_path}`

**Acceptance Criteria:**
- [ ] Complete {OrchestratorName} coordinating all managers
- [ ] All delegation methods routing to appropriate managers
- [ ] Cross-manager interaction methods implemented
- [ ] System health monitoring aggregating from all managers
- [ ] Comprehensive test coverage
- [ ] Follows established orchestrator pattern (manager coordination, not direct service coordination)
- [ ] Clean separation: orchestrator coordinates managers, managers coordinate services
```

#### For Bug Reports:

```markdown
**Bug Description:**
{Clear description of the bug}

**Expected Behavior:**
{What should happen}

**Actual Behavior:**
{What actually happens}

**Steps to Reproduce:**
1. {Step 1}
2. {Step 2}
3. {Step 3}

**Environment:**
- OS: {operating system}
- Python version: {version}
- Package version: {version}
- Relevant dependencies: {list}

**Error Messages/Logs:**
```
{paste error messages or logs}
```

**Possible Cause:**
{If known, suggest what might be causing it}

**Suggested Fix:**
{If known, suggest how to fix it}

**Priority**: {HIGH | MEDIUM | LOW}

**Files Affected:**
- `{file_path_1}`
- `{file_path_2}`
```

#### For Feature Requests:

```markdown
**Feature Description:**
{Clear description of the feature}

**Use Case:**
{Why is this feature needed? What problem does it solve?}

**Proposed Implementation:**
{How should this feature work?}

**Benefits:**
- {Benefit 1}
- {Benefit 2}

**Potential Challenges:**
- {Challenge 1}
- {Challenge 2}

**Alternative Approaches:**
{Other ways to solve this problem}

**Priority**: {HIGH | MEDIUM | LOW}

**Milestone:** {target version}

**Files to Modify/Create:**
- `{file_path}`
```

**Present the structured draft to the user for review before proceeding to Phase 3.**

### Phase 3: Validation

Show the user the complete structured issue and ask:

1. **Review Purpose**:
   - Is the purpose statement accurate?
   - Does it capture the full scope?
   - Options: [y/n/edit]

2. **Check Dependencies**:
   - Are all dependencies listed?
   - Do issue links (#XX) reference the correct issues?
   - Options: [y/n/add]

3. **Verify File Location**:
   - Is the file path correct?
   - Does it follow project conventions?
   - Options: [y/n/fix]

4. **Review Code Snippets**:
   - Do integration patterns look correct?
   - Are class names and methods appropriate?
   - Options: [y/n/adjust]

5. **Confirm Labels**:
   - Current labels: {show current labels}
   - Add/remove any? Options: [y/n]

6. **Verify Milestone**:
   - Milestone: {current milestone}
   - Correct? Options: [y/n/change]

7. **Final Confirmation**:
   - Ready to create the issue?
   - Options: [yes/no/review again]

**Allow iterative refinement:** If user says "no" or "edit", ask what needs to change and loop back through the relevant validation questions.

### Phase 4: Creation

Once user confirms, execute the following:

1. **Save Issue Body to Temporary File**:
   ```bash
   # Create temp file with issue body
   Write temp_issue_body.md with structured content
   ```

2. **Create GitHub Issue**:
   ```bash
   # Create issue and capture issue URL
   issue_url=$(gh issue create \
     --repo {selected_repository} \
     --title "{issue_title}" \
     --body-file temp_issue_body.md \
     --label "{label1,label2,label3}" \
     --milestone "{selected_milestone}")

   # Extract issue number from URL
   issue_number=$(echo $issue_url | grep -oP '\d+$')
   ```

   **Use values from Phase 1:**
   - `{selected_repository}`: Repository chosen by user (or default from detection)
   - `{selected_milestone}`: Milestone chosen by user (or default from detection)
   - `{issue_title}`: Generated from component type and name
   - `{labels}`: Selected/confirmed in Phase 3

3. **Add Issue to Project and Set Iteration**:
   ```bash
   # Add issue to project
   item_id=$(gh project item-add {project_number} \
     --owner {owner} \
     --url "${issue_url}" \
     --format json | jq -r '.id')

   # Set iteration field on the project item
   gh project item-edit \
     --id "${item_id}" \
     --project-id {project_id} \
     --field-id {iteration_field_id} \
     --text "{selected_iteration}"
   ```

   **Use values from Phase 1:**
   - `{project_number}`: Default "match_table_package" project number
   - `{owner}`: Repository owner (e.g., "amielsaa")
   - `{project_id}`: Full project ID (get from project details)
   - `{iteration_field_id}`: Iteration field ID from project
   - `{selected_iteration}`: Iteration chosen by user

4. **Clean Up**:
   ```bash
   # Remove temporary file
   rm temp_issue_body.md
   ```

5. **Return Results**:
   - Issue URL
   - Issue number
   - Repository used
   - Milestone assigned
   - Project added to
   - Iteration set
   - Confirmation message

**Example output:**
```
✅ Successfully created GitHub issue!

Issue #147: Implement Cross-Component Interaction Service
URL: https://github.com/amielsaa/match_table_package/issues/147

Repository: amielsaa/match_table_package
Milestone: v1.0.0 - Initial Release
Project: match_table_package
Iteration: Iteration 2
Labels: enhancement, high-priority, data-service, visualization
```

## Best Practices

- **Always ask all discovery questions** - Don't skip or assume
- **Use appropriate template** - Match component type to template structure
- **Include complete code snippets** - Show class structure and key methods
- **Reference related issues** - Use #XX format for dependencies
- **Validate before creation** - Always confirm with user
- **Clean up temp files** - Remove temporary issue body files
- **Return clear confirmation** - Show issue URL and number

## Examples

### Example 1: Creating a Data Service Issue

**User Request:**
"Create an issue for a new pathway visualization service"

**Phase 1 - Discovery:**
```
Assistant: I'll help you create a GitHub issue for the pathway visualization service.

1. Component Type: Is this a data service?
User: Yes

2. Brief Description: What does this service do?
User: Retrieves pathway data and generates pathway visualization information

3. Main Responsibilities:
User:
- Fetch pathway data from KEGG
- Map compounds to pathway positions
- Generate pathway URLs with highlighting

4. Dependencies: What does this depend on?
User: Issue #99 (ExtendedDataService) and reference_service

5. Priority: HIGH, MEDIUM, or LOW?
User: HIGH

6. Milestone:
User: v1.0.0 - Initial Release

7. File Location:
User: src/metabolomics_pipeline/visualization/visualization_data/pathway_viz_service.py

8. Additional context?
User: Should integrate with existing reference_service for KEGG data
```

**Phase 2 - Structuring:**
Assistant generates complete issue following Data Service template with:
- Purpose statement
- Dependencies (#99, reference_service)
- Integration pattern code snippet
- Required methods list
- Implementation checklist
- Testing plan
- Acceptance criteria

**Phase 3 - Validation:**
```
Assistant: Here's the structured issue. Let me verify:

1. Purpose accurate? "Retrieve pathway visualization data..."
User: Yes

2. Dependencies complete? #99, reference_service
User: Yes

3. File location correct? src/metabolomics_pipeline/visualization/visualization_data/pathway_viz_service.py
User: Yes

4. Labels: enhancement, high-priority, data-service, visualization
User: Yes

5. Milestone: v1.0.0 - Initial Release
User: Yes

6. Ready to create?
User: Yes
```

**Phase 4 - Creation:**
```
Assistant executes:
1. Writes temp_issue_body.md
2. Runs: gh issue create --repo user/repo --title "Implement Pathway Visualization Service" --body-file temp_issue_body.md --label "enhancement,high-priority,data-service,visualization" --milestone "v1.0.0 - Initial Release"
3. Removes temp_issue_body.md
4. Returns:

✅ Successfully created GitHub issue!

Issue #150: Implement Pathway Visualization Service
URL: https://github.com/user/repo/issues/150

Labels: enhancement, high-priority, data-service, visualization
Milestone: v1.0.0 - Initial Release
```

### Example 2: Creating a Manager Issue

**User Request:**
"Create issue for VisualizationDataManager"

**Workflow:**
- Phase 1: Discover it's a manager coordinating 5 services
- Phase 2: Apply Manager template, emphasize thin delegation
- Phase 3: Validate dependencies (list all 5 service issues)
- Phase 4: Create with labels: enhancement, high-priority, visualization, integration

**Result:** Manager issue with proper delegation pattern documented

### Example 3: Creating a Bug Report

**User Request:**
"File a bug - tests are failing when database isn't cleared"

**Workflow:**
- Phase 1: Gather bug details (expected vs actual, reproduction steps)
- Phase 2: Apply Bug Report template
- Phase 3: Validate error messages and affected files
- Phase 4: Create with labels: bug, high-priority

## Security Considerations

- **Never hardcode credentials**: Use gh CLI authentication
- **Validate repository URLs**: Confirm before creating issues in repos
- **Clean up temporary files**: Always remove temp_issue_body.md
- **Sanitize user input**: Validate issue titles and descriptions
- **Respect permissions**: Only create issues in repositories user has access to

## Troubleshooting

### Issue: gh CLI not authenticated
**Solution:**
```bash
# Authenticate gh CLI
gh auth login
```

### Issue: Labels don't exist in repository
**Solution:**
- Create labels first via GitHub UI or:
```bash
gh label create "enhancement" --color "0E8A16"
gh label create "high-priority" --color "D93F0B"
```

### Issue: Milestone not found
**Solution:**
- Create milestone first via GitHub UI or:
```bash
gh milestone create "v1.0.0 - Initial Release"
```

### Issue: Template doesn't match component type
**Solution:**
- Ask user if they want to use a different template
- Offer to customize the template
- Allow manual editing before creation

### Issue: User wants to edit after creation
**Solution:**
- Provide gh CLI edit command:
```bash
gh issue edit {issue_number} --body-file updated_body.md
```

## Tips for Success

1. **Be thorough in discovery** - The better the input, the better the output
2. **Show examples during validation** - Help user visualize the final issue
3. **Explain template choices** - Why Manager template vs Service template
4. **Confirm destructive actions** - Always validate before creating
5. **Provide follow-up guidance** - How to edit, how to link issues, etc.

## Next Steps After Skill Completes

After creating an issue, suggest:
1. **Link related issues** - Create dependency relationships
2. **Notify team members** - @mention relevant people
3. **Add to project board** - Organize in kanban/project view
4. **Create implementation branch** - Start working on the issue

---

**Remember:** This skill automates the formatting and creation, but the quality of the issue depends on the quality of information gathered in Phase 1. Take time to understand what the user needs!
