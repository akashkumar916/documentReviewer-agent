# claude-document-reviewer

A [Claude Code](https://claude.com/claude-code) subagent that gives structured, critical feedback on documents.

It handles:
- SOPs / personal statements (including PhD-specific checks)
- Resumes and academic CVs
- Academic research papers
- Industry / enterprise papers (agentic AI, platform architecture, user studies)
- Cover letters and other reports

It detects the document type and the mode (author feedback vs. reviewer report), applies the matching checklist, and can cross-check an SOP, CV and paper for consistency. It never modifies your files.

## Install

Copy the two files into your Claude Code config folder:

```bash
git clone https://github.com/akashkumar916/claude-document-reviewer.git
cd claude-document-reviewer
mkdir -p ~/.claude/agents ~/.claude/commands
cp document-reviewer.md ~/.claude/agents/
cp docreview.md ~/.claude/commands/
```

For one project only, copy them into that project's `.claude/agents/` and `.claude/commands/` instead.

Restart Claude Code (or start a new session) so it picks them up.

## Use

```
/docreview ~/Documents/sop.pdf PhD Information Science, 1000-word limit, I'm the author
/docreview ~/cv.pdf ~/sop.docx        # several files: adds a cross-document consistency check
/docreview ~/paper.pdf I'm reviewing for the AI-Native Experiences track
```

You can also ask in plain language ("review my SOP at ~/sop.docx"), and Claude will delegate to the `document-reviewer` agent.

## Notes

- `.docx` files are converted with `textutil` (macOS) or `pandoc`, so one of them must be installed on other platforms.
- The agent treats unpublished and internal documents as confidential. Web searches use general topic terms only, never manuscript text or titles.
- It reports what it can verify. Facts about people, papers and links are flagged as unverified unless checked.
