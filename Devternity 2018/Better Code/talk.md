# 12 ways to improve your code
> By Venkat Subramaniam

1 Schedule Time to Address Technical Debt
 - Writing bad code to begin with is not tech debt, it's intentional sabotage
 - Have the known debt visible so it can be addressed

2 Favour High Cohesion
 - High cohesion results in low cyclomatic complexity and becomes much easier to understand. Refactor when needed to improve this.

3 Favour Loose Coupling
 - Interfaces make it ease to decouple
 - Eliminate coupling where possible

4 Program with Intention
 - Ensure you understand what you're doing and why you're doing it

5 Avoid Primitive Obsession
 - If it's domain specific, you write the code. If it's not, someone else have probably already done a better job
 - Code should read like a story, not a puzzle

6 Prefer Clear Code over Clever Code
 - Often the simplest solution is the best
 - Programs must be written for people to read and computers to run

 7 Apply Zinsser's Principle of Writing
  - William Zinsser 'On Writing Well'
  - Simplicity, Clarity, Brevity, Humanity

8 Comment Why, not What
 - `i++ //increment` :(
 - Good code should be like a good joke. You shouldn't have to explain it. Comments should only be there to explain why the code exists, not what it does.

9 Avoid Long Methods - Apply SLAP
 - Single Level of Abstraction Principle
 - Long isn't lines, but levels of abstration and complexity
 - Methods should be composed of instructions at a single level of abstraction

10 Give Good Meaningful Names
 - Variables should be meaningful and descriptive

11 Do Tactical Code Reviews
 - Reviews should be shared across the team
 - Review often and frequently

12 Reduce State and State Mutation
 - The more state there is, the harder it is to maintain