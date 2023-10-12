# How to Conduct a Code Review

**Golden Rule:** Critique the code, not the author

## What to look for

- Design
- Functionality (including performance & security)
- Complexity
- Tests
- Naming
- Comments
- Style
- Documentation

Source: [Google's The Code Reviewer’s Guide](https://google.github.io/eng-practices/review/reviewer/looking-for.html)

## During the review

Consider:

- Does it meet all the requirements?
- Is it readable and maintainable?
- Is it fast enough and secure enough?
- Does it need additional documentation?
- Is my comment clear, necessary, helpful, and actionable?

## Steps to a review

1. Read the description & requirements
2. Review the tests
3. Review the code (broadly, then line-by-line)
4. Manual testing for requirements
5. Add comments

## Labeling comments

- Trivial => minor, non-blocking, optional
- Suggestion => improvement, non-blocking or blocking
- Issue => blocking, should include an explanation and guidance 

\*Blocking means preventing approval

## Example comments

```
# Bad
Make this name better 
Doesn't follow style guide OR best practices
Explain this to me 
You can't do this 
Fix this so it's more readable
You should write a comment, because this class doesn't read easy

# Good
trivial - consider a more concise variable name
suggestion (blocking) - use find_in_batches for improved memory consumption 
suggestion (non-blocking) - consider writing a comment for quicker understanding of the class
issue - this could be a security vunerability, let's talk about it on Slack
issue - this method is deprecated, consider X as an alternative 
issue - avoid default_scope because it hides behavior and could introduce bugs, use explicit scopes instead 
```

## How to prevent conflicts

Automated static code analyzers can help mitigate style, readability, and even security issues. Analyzers also help
prevent potential conflicts between reviewers and authors. Developers rarely feel attacked by linters. Automating this process
allows code reviews to focus on big-picture issues and teach developers new techniques.

Being respectful is a reviewer's best tool for preventing personal conflicts with authors. Explaining your comments is another tool
to promote understanding between the reviewer and author. Clarity on severity (i.e. using labels) helps authors understand what must, should, and could be fixed or improved.

Reviewers should avoid making the comments personal. Avoid using "you" or "I" in comments. "Why did you do it like this?" or "I won't have done it like this" are not actionable and not helpful.
Asking a clarifying question is completely acceptable: "Can you explain this method?".

Part of a review's purpose is to provide guidance. Ask yourself, is this comment helpful? "Don't do this" isn't actionable. "trivial - Consider X instead of Y" tells
the author a few things. First, the comment is minor and non-blocking. Second, an alternative approach. Third, the author could use a different approach that might still be acceptable.

Consulting PRDs, style guides, or data can help remove opinions or preferences from comments.

## How to resolve conflicts

If a conflict in approach arises, discussing the issue outside of the code review (in-person or virtually) is usually a good idea. The goal is to reach a consensus. If a consensus can't
be reached, the next best thing to do is escalate the issue to a lead/staff engineer or even an engineering manager.
