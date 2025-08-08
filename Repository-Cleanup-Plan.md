# AIExplore Repository Cleanup Plan

## Overview
A systematic approach to clean, consolidate, and organize the AIExplore knowledge repository, combining AI analysis with human review for optimal results.

## Phase 1: Discovery & Analysis (AI-Led)

### 1.1 Duplicate Detection
**AI Tasks:**
- Scan all markdown files for similar titles and content
- Identify files with >70% content similarity
- Flag potential duplicates based on:
  - Similar filenames (e.g., "Claude Cheat Sheet.md" vs "Claude scaffolding cheat sheet.md")
  - Overlapping topics across directories
  - Multiple versions of the same guide

**Human Review:**
- Confirm which duplicates to merge
- Decide primary version to keep
- Identify unique valuable content to preserve

### 1.2 Content Freshness Analysis
**AI Tasks:**
- Identify dated references (e.g., "GPT-3" when GPT-4 exists)
- Flag model version references that are outdated
- Find broken methodology references (deprecated tools/APIs)
- Detect time-sensitive content (e.g., "coming in 2023")

**Human Review:**
- Verify what's actually outdated vs. historically valuable
- Decide what to update vs. archive vs. delete

## Phase 2: Content Quality Review (Human-Led, AI-Assisted)

### 2.1 Accuracy Check
**AI Tasks:**
- Flag technical inaccuracies based on current knowledge
- Identify conflicting information across documents
- Highlight deprecated practices or tools

**Human Review:**
- Verify AI's accuracy assessments
- Provide context for apparent contradictions
- Decide on authoritative versions

### 2.2 Relevance Assessment
**Human Tasks:**
- Review "To investigate.txt" and similar holding files
- Assess value of draft/incomplete documents
- Identify core vs. peripheral content

**AI Support:**
- Summarize long documents for quick review
- Suggest categorization improvements
- Identify orphaned or unreferenced files

## Phase 3: Consolidation (AI-Led with Human Approval)

### 3.1 Merge Strategy
**AI Tasks:**
- Create consolidated versions of duplicate content
- Preserve unique sections from each duplicate
- Maintain best practices from all versions
- Generate merge proposals for review

**Human Review:**
- Approve/modify proposed merges
- Ensure no valuable content is lost
- Verify consolidated version is coherent

### 3.2 Directory Consolidation
**Current Issues to Address:**
- Multiple AI tool guides scattered across directories
- Prompting strategies in multiple locations
- Overlapping "cheat sheets" and "tutorials"

**Proposed Structure:**
```
AIExplore/
├── Core-References/           # Essential, frequently-used guides
│   ├── Tool-Guides/          # Claude, ChatGPT, Copilot, etc.
│   ├── Prompting-Strategies/
│   └── Development-Setup/
├── Research-Archive/          # Historical, theoretical, philosophical
├── Project-Ideas/            # Application ideas and plans
├── Learning-Resources/       # Tutorials, courses, how-tos
└── Workflows/               # Productivity and process docs
```

## Phase 4: Enhancement (AI-Led)

### 4.1 Navigation Improvements
**AI Tasks:**
- Generate README.md for each major directory
- Create comprehensive index/TOC
- Add "Related Documents" sections
- Generate tag-based categorization

### 4.2 Cross-Referencing
**AI Tasks:**
- Identify related documents
- Add bidirectional links between related content
- Create topic maps
- Generate "See Also" sections

## Phase 5: Maintenance System (Human-Defined, AI-Assisted)

### 5.1 Version Control Strategy
- Archive outdated but historically valuable content
- Create "Last Updated" timestamps
- Establish review cycles for time-sensitive content

### 5.2 Ongoing Maintenance
- Quarterly freshness reviews
- New content integration guidelines
- Duplicate prevention strategies

## Execution Timeline

### Week 1: Discovery
- [ ] Run duplicate detection
- [ ] Generate staleness report
- [ ] Create initial cleanup recommendations

### Week 2: Review & Decisions
- [ ] Human review of AI findings
- [ ] Make keep/merge/delete decisions
- [ ] Prioritize high-value consolidations

### Week 3: Consolidation
- [ ] Execute approved merges
- [ ] Reorganize directory structure
- [ ] Update file locations

### Week 4: Enhancement
- [ ] Add navigation aids
- [ ] Create cross-references
- [ ] Generate master index

## Specific Areas Needing Attention

### High Priority
1. **Multiple Claude/ChatGPT guides** - Need consolidation
2. **Scattered prompting strategies** - Should be unified
3. **Dev setup guides** - Mix of tools, versions, approaches
4. **Agent documentation** - Multiple versions in Agents-file/

### Medium Priority
1. **Image prompt guides** - Could be consolidated
2. **Research notes** - Need freshness review
3. **Application ideas** - Some may be stale

### Low Priority
1. **Historical/philosophical content** - Mostly archival
2. **Personal productivity notes** - User-specific

## Success Metrics
- Reduce file count by ~30% through consolidation
- No duplicate information across files
- Every file accessible within 3 clicks from root README
- All technical content accurate as of 2025
- Clear separation of current vs. archival content

## Tools & Automation

### AI Tools to Use
- Content similarity detection
- Broken link checking
- Outdated reference detection
- Auto-generation of TOCs and indexes

### Human Decision Points
- Final merge approvals
- Content deletion decisions
- Organizational structure changes
- Quality verification

## Next Steps
1. Review and approve this plan
2. Begin Phase 1 discovery scan
3. Create backup before any deletions
4. Set up review schedule for findings