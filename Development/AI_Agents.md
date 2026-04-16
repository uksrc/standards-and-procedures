Working with AI Agents
======================

working with AI agents can be a powerful way to accelerate development, but it is important to use them in a way that is effective and efficient. Here are some tips for working with AI agents:


* Ask the agent to create a plan for how to solve the problem. This can help you to understand the agent's thought process and to identify any potential issues with the solution.
   - Iterate on the plan with the agent, asking it to refine and improve the plan as needed. This can help to ensure that the solution is well thought out and that it addresses all of the relevant aspects of the problem.
   - Once you have a plan that you are happy with, ask the agent to implement the solution. This can help to speed up the development process and to ensure that the solution is implemented correctly.
* Thoroughly review the solution that the agent has implemented before actually merging it into your main branch.

## Agents have some bad habits

* Don't allow them to write tests at the same time as writing code, they will often write tests that are not actually testing anything, or that are testing the wrong things. 
  * If you have some existing code without tests then you can ask the agents to write tests for that code, but do not let them change the implementation at the same time.
    
* They will often create a new function rather than reuse existing code, even if the existing code is perfectly suitable for the task at hand. This can lead to a proliferation of functions that are not actually needed, and can make the codebase more difficult to maintain.
  * If you have existing code that is suitable for the task at hand, then you can ask the agent to reuse that code rather than creating a new function.

* The can get stuck in a sort of doom loop where they cannot figure out how to simultaneously make two tests pass, breaking the other each time they make one pass. In this case it can be helpful to ask the agent to focus on making one test pass at a time, rather than trying to make both tests pass simultaneously. 
  * It is worth monitoring the agent's progress and intervening if it seems to be getting stuck in a loop. 
  * This sort of doom loop with tests can be an indication that there is something wrong with the tests of course.