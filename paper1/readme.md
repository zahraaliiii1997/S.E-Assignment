# A Case Study on Tool Support for Collaboration in Agile Development

## Authors

+ Fabio Calefato
+ Andrea Giove
+ Filippo Lanubile
+ Marco Losavio

***Conference Name:*** IGCSE – 2020

***Introduction And Motivation:***
Agile development is an increasing trend for software organizations, whether small or large, working co-located or geographically distributed. Still, there are many challenges in supporting effective collaboration and communication for agile teams. This research aims at studying the Agile work environment at Klopotek to identify points of friction between development practices and collaboration tools. As such, we are interested in answering the following research question: How can the Agile work environment be improved to facilitate communication and better support the collaboration workflow?

***Research methodology:***

+ Researchers first Studied the Agile work environment at Klopotek to identify points of friction between development practices and collaboration tools.
+ The data was collected by four main data sources.
  + Documentation.
  + Direct observations.
  + Tools.
  + Interview.

***Klopotek:*** Software & Technology Services Italia was opened with the specific goal of redeveloping the legacy ERP desktop application into a cloud-based web application, called Stream. Klopotek Deployment Manager, a tool used both internally and by customers to install and configure Klopotek solutions without manual intervention, and Core, a framework that allows both the web app and the legacy tool to interact with the back-end via a RESTful API.

***Development Process:***

The development & test activities involve periodic Grooming and here participants make estimations of user stories based on the development time. The tools can be broadly grouped into three main categories, that is,

+ Development
+ infrastructure management
+ collaboration

Other than Skype, Klopotek has adopted Slack as the means of site-specific, technical-oriented communication. There are two separate workspaces, one for each of the two development sites. Regarding KSTS-It, Slack is mostly used for quick questions, code snippet and file sharing, and one to one communication.

***Changes:*** Mainly two basic changes were observed.

***First Change***

***(Reinforcing the Use of Slack):***

The focus of the first change was on reinforcing the use of Slack as a central hub for internal communication. To counteract the communication issues that emerged from the interviews and direct observation, during the change, Slack became the tool of choice for channeling all the internal communication.
Please, note that, other than the new three channels, the Slack configuration during the execution of the first change also included the previously existing channels reported in Table 3, which we did not analyze.

![table 3](/paper1.jpg)

Finally, to ensure that all the participants used the tool as intended during the change, we added to Confluence a new documentation page about Slack, with channel descriptions, instructions, and advice for a proper use such as avoid using direct messages and creating new private channels for communication relevant for a whole team.

***Quantitative Analysis Results:***
To understand what kind of information was exchanged in the channels during the Sprint, we manually performed the content analysis of the messages using the coding schema designed by Stray et al.
The coding schema is reported for convenience in Table 4.

![table 4](/table4.jpg)

The coding was performed iteratively by the first two authors. In the first iteration, we randomly selected a sample of 40 thematic units. Each thematic unit was obtained by identifying in the log a set of messages sent by one user, which have the same intent even if split into multiple, non-consecutive utterances. Otherwise, had we chosen a few random messages and ignored their 'context,' the coding procedure would have been impossible. Furthermore, we selected several thematic units from each of the three channels proportional to the overall number of messages sharing therein during the experiment. The second iteration followed a similar process on a new set of 40 thematic units. Because the measured inter-rater agreement was high, after resolving the disagreements, we decided that the remaining units could be safely coded by one coder only. The most common intents for communicating were sharing Technical Information and resolving issues. A very few messages were exchanged for general-purpose Q&A, to coordinate, and socialize. #sprints, further proof of improper use of the latter channel.

***Qualitative Analysis Results.***
At the end of the Sprint, Few interviews were conducted with 13 participants to get feedback about how the use of Slack affected internal communication at KSTS-It.
First, we asked whether they happened to send emails and, if so, why. We found out that only 4 out of 13 fully complied with the instructions and used Slack instead of using 'internal' emails. , users had the perception that Slack was better suited for short, instant messages and, hence, the use of emails was preferred for longer, more complex communication like discussing a feature from the current Sprint.

+ Very unuseful,
+ Somewhat unuseful,
+ Neither useful nor unuseful,
+ Somewhat useful,
+ Very useful.
The #qa channel was the most appreciated, as 9 respondents found it Very or Somewhat useful. Slack notifications «things are much faster and more immediate than emails». Concerning #sprints, the evaluation was slightly less positive than #qa, with 7 respondents finding it Very or Somewhat useful, and 3 who thought it was Somewhat unuseful.
When interviewed, the participants said that they saw potential in it but also that the channel would «take more than a Sprint to come to fully understand its benefits» and it would likely become «more useful over time». Therefore, we decided to collect survey responses from the same participants again, after another Sprint. 5 shows that the participants were more favorable to Slack than email, with no one feeling unsatisfied about the former.

***Second Change:***

***Multiple Scrum Boards and Jira Automation***

In the second change, researchers focused on improving the collaboration workflow in Jira. This new board shows only the main user stories, tasks, and bug reports, and provides at a glance a picture of how the current Sprint is going, with the original board showing the detailed sub-tasks useful for the Dev and QA teams.
The other proposed improvement was the installation of Automation for Jira, a third-party Slack plugin that allows the definition of automation rules in the form event–condition–action.

***Quantitative Analysis Results:***
The #dev channel received 267 messages and 87 mentions from 17 users, with an overall increase compared to the first observation. Most of these messages are notifications from the Jira automation plugin, such as 'user story ready to test' or 'bug resolved' with explicit mentions of some QA team members. Problem-focused Communication. 316 messages and 54 mentions from 19 users.

***Qualitative Analysis Results:***
At the end of the Sprints, researchers interviewed all the twenty participants. From these follow-up interviews, they found that the high-level board was not used and appreciated by Management to the expected extent. They also asked them to rank the ten automation rule in descending order of usefulness. The results are reported in Table 5 aggregated per team and overall.

![table 5](/paper1.png)

The top three ranked rules are ready_to_test, start_implementation, and. Thanks to the plugin, 85% of the interviewees found their workflow to be improved, and the remaining found it unaffected by it.
Also, all participants were recommended to set their preferences to direct messages, mentions & keywords not to miss any relevant notification.

***Slack as a Central Hub of Communication:***

Slack as the central hub for internal communication, while setting clear rules regarding other tools and channel usage. Slack fosters communication transparency. Thanks to the use of public channels for sharing team-relevant pieces of information, the new Slack configuration introduced helped to make communication at KSTS-It more 'transparent. Overall, KSTS-It teams liked using Slack as a central hub of communication and used it mostly problem-solving.

***Jira Boards and Automation Rules***

As a second chance, we added to Jira a new high-level Scrum board while also introducing automation rules and notifications to Slack. Managers need more time to adjust. Overall, the ten automation rules introduced in Jira were found useful, with 85% of participants reporting a more streamlined workflow thanks to them. Besides, while automation rules may not be as useful for everyone, they are detrimental to no one.
As such, KSTS-It is considering expanding the set of automation rules also to other tools.

***_Limitations_***

A second limitation relates to potential bias in our data collection. Some data was based on direct observations and semistructured interviews conducted by one of the authors. However, to reduce bias, multiple data sources were used to triangulate relevant pieces of information, and a protocol was agreed upon before conducting the interviews.

 ***_CONCLUSIONS AND FUTURE WORK_***

In this paper, we reported on a case study conducted at KSTS-It, the Italian site of a large, distributed software company. We found out that, overall, KSTS-It accepted the restructured Slack workspace and the Jira automation rules, and reported more improvements in their communication and workflow.
Finally, they are considering also bringing to Berlin some of the changes investigated at the Italian site.

***_results:_***

+ The first change revealed that the teams of developers used and appreciated Slack differently with the QA team being the most favorable and that the use of channels is hindered by automatic notifications from development tools (e.g., Jenkins).
+ We report on a longitudinal case study conducted at the Italian site of a large
software company to further our understanding of how development and communication tools can be improved to better support agile practices and collaboration.
+ As a second main change, we refactored the Jira Scrum board into two separate boards, a detailed one for developers and a high-level one for managers, while also introducing automation rules and the integration with Slack.
+ After observing inconsistencies in the way communication tools (i.e., email, Skype, and Slack) were used, we first reinforced the use of Slack as the central hub for internal communication, while setting clear rules regarding tools usage.
