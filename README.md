#Let's Turn Slack Into A Database

Everyone in your (my) company uses Slack. On the internal tools team at Loblaw Digital, we use Slack as a direct portal to our clients, who just so happen to be our colleagues. Why wouldn't we take advantage of this platform with great developer tools to reduce toil, increase hapiness, and get shit done quicker and easier for our friends. We call it ChatOps and our team's main product is Jeanie, a Slack app who hosts a bevy of tools that our coworkers use on a daily basis. 

Something you probably don't know about Loblaw Digital is that we have a company wide house cup tournament (kinda like Hogwarts) going on all year-round. Points are awarded for participating in activies and contests but we never really had an easy way to look up the current scores. So when we were given a day to participate in a company hackathon, we jumped at the chance to add this feature to Jeanie. We wanted the Tournament Master to be able to update points through Slack and anyone else to be able to look up the scores. The implementation wasn't too difficult until we ran into the issue of persistent storage. Why on Earth would you spin up a database on your cluster just to store 4 numbers? We couldn't justify it. That's when we had the idea to use Slack as our database. 

The first incarnation of SlackDB was just a private channel 

