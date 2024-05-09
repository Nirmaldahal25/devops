# Running ansible playbook
- Run `ansible-playbook <file.yml>` add priviliges escalation arguments after this command.
- We can run ansible for certain tages. ie, `ansible-playbook --tags "<tag1>,<tag2>,..." <file.yml>`
- In this ansible project, I have used copy, package modulee. Assigned group, user to the file. Also ansible has records of states that triggers handlers on change. This event can be used in starting services or handling dependencies/prerequisities.

