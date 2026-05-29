# Contributing to the QA Tool Kit

Contributions are welcome. This toolkit gets better with feedback from people who use it in the field.

---

## Ways to contribute

### Report a problem with a prompt
If a prompt produces poor output, missing coverage, or behaves unexpectedly — open an issue. Include:
- Which prompt (number and name)
- What you were trying to do
- What the model produced vs what you expected
- The LLM you were using (Claude, ChatGPT, etc.)

### Suggest an improvement
If you have adapted a prompt for your stack and the changes made it significantly better, open an issue or pull request describing what you changed and why.

### Propose a new prompt
Have a recurring QA task that isn't covered here? Open an issue with the title `[New Prompt] — <name>` and describe the problem it would solve.

---

## Pull request guidelines

1. One prompt or improvement per pull request — keep changes focused
2. Follow the existing file structure:
   - Each prompt lives in `/prompts/` as its own markdown file
   - Use the naming convention `0X-prompt-name.md`
   - Include: prompt text in a code block, required inputs table, optional modifiers list
3. Test your prompt against at least two LLMs before submitting
4. Update `CHANGELOG.md` with a one-line description of what changed

---

## What will not be merged

- Prompts that are not grounded in real QA workflows
- Changes that make prompts more generic rather than more specific
- Content that oversimplifies or talks down to QA engineers

---

## Contact

Questions before submitting? Kindly reach out via email. 