---
description: Review an SOP, resume/CV, research paper, industry paper, or other document with the document-reviewer agent
argument-hint: <file path(s)> [context, e.g. "PhD Info Sci, US" or "I'm reviewing for AI-Native Experiences track"]
---

Use the Agent tool with `subagent_type: "document-reviewer"` to review the document(s) below.

Request: $ARGUMENTS

Instructions:
- If no file path or document text is given above, ask the user which document to review and stop.
- Expand `~` and resolve relative paths to absolute paths before passing them to the agent. If a path doesn't exist, use Glob to find a close match. If nothing matches, tell the user.
- Pass the agent every file path plus all the context the user gave (target program/role/venue/track, word limits, deadline, whether they are the author or a reviewer).
- If several files are given, send them to **one** agent call, so it can run the cross-document consistency check.
- Show the agent's full review to the user exactly as returned. Don't summarize or shorten it.
