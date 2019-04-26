# Let's Turn Slack Into A Database (working title)

Everyone in your (my) company uses Slack. On the internal tools team at Loblaw Digital, we use Slack as a direct portal to our clients, who just so happen to be our colleagues. Why wouldn't we take advantage of this platform with great developer tools to reduce toil, increase hapiness, and get shit done quicker and easier for our friends. We call it ChatOps and our team's main product is Jeanie, a Slack app who hosts a bevy of tools that our coworkers use on a daily basis. 

Something you probably don't know about Loblaw Digital is that we have a company wide house cup tournament (kinda like Hogwarts) going on all year-round. Points are awarded for participating in activies and contests but we never really had an easy way to look up the current scores. So when we were given a day to participate in a company hackathon, we jumped at the chance to add this feature to Jeanie. We wanted the Tournament Master to be able to update points through Slack and anyone else to be able to look up the scores. The implementation wasn't too difficult until we ran into the issue of persistent storage. Why on Earth would you spin up a database on your cluster just to store 4 numbers? We couldn't justify it. That's when we had the idea to use Slack as our database. 

The first incarnation of SlackDB was simply a private channel to which Jeanie would post a json containing the current state of Tournament points. Whenever called upon, she could just read from the most recent post in the channel's history. That was it. We didn't have to spin any pods up. We didn't need a local dev server. Slack had us covered. In this endeavour, we also noticed that our 'database' had built-in version control and rollbacks. The entire history of point allocations was up for display and we could revert to a previous state by deleting posts. Then we got thinking: what if we could turn Slack into an actual database? The idea got put on hold.

A few weeks later, one of our coworkers suggested an acronym bot for our Slack workspace. There were so many acronyms flying around that it was hard to keep up. 

> <INSERT A SENTENCE WITH A BUNCH OF ACRONYMS>
What the fuck??
  
The goal was to allow users to select a message and get Jeanie to give them a run down of whatever acronyms were used. We also wanted a way to croudsource the acronyms and use a voting system to settle disputes. Honestly, we could have done it with a regular database and a web front-end (and the UX would have suffered for it) but we used this as an excuse to build SlackDB.

So how do you go about using Slack as a database?


