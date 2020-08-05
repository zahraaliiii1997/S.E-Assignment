# Data Loss Detector: Automatically Revealing Data Loss Bugs in Android Apps

## authors

+ Oliviero Riganelli
+ Simone Paolo Mottadelli
+ Claudio Rota
+ Daniela Micucci
+ Leonardo Mariani

***Conference Name:*** ISSTA ’20

***Introduction:*** Data loss faults may affect the correctness of the apps in many different ways. Data loss faults can be extremely pervasive. Some techniques have been designed to extend the fault discovery capability of existing test suites to data loss problems. ALARic can successfully reveal data loss faults, but the adopted exploration strategy and oracles have limited effectiveness, as reported in our evaluation. DLD automatically detected 83 of the 110 data loss problems. DLD also revealed 35 data loss faults that were not part of the benchmark, but were reported online in bug reports, and 232 previously unknown data loss faults. Overall DLD revealed three times the data loss faults revealed by competing approaches. Data loss faults may affect the correctness of the apps in many different ways. Data loss faults can be extremely pervasive. Some techniques have been designed to extend the fault discovery capability of existing test suites to data loss problems. ALARic can successfully reveal data loss faults, but the adopted exploration strategy and oracles have limited effectiveness, as reported in our evaluation. DLD automatically detected 83 of the 110 data loss problems. DLD also revealed 35 data loss faults that were not part of the benchmark, but were reported online in bug reports, and 232 previously unknown data loss faults. Overall DLD revealed three times the data loss faults revealed by competing approaches.

__Motivation__ 

***Research methodology:***

This paper is organized as follows.

+ discusses data loss faults and exemplifies typical failures that can be experienced with Android apps. 

+ describes the main technical contributions of this paper, including the biased model-based exploration strategy, the data-loss-revealing actions, and the automatic oracles. Section 4 reports empirical results.

+ discusses related work.

+ provides final remarks.

***DATA LOSS FAULTS***
To partition a screen into smaller units, activities can contain a number of fragments, each one containing both some graphical elements and the logic to handle them. Both activities and fragments have their own lifecycle . Specific sequences of system events may have a direct impact on the lifecycle of activities and fragments. A stop-start event is a sequence of system events that may cause a running activity to be destroyed and then recreated1.
Stop-start events are generated when the execution of an activity must be temporarily suspended. There are many common situations that produce stop-start events. For instance, answering a phone call requires suspending the execution of the app, and thus also of the current activity, until the call ends. Moving an app to the background may cause its activities to be destroyed.
When the app is moved again to the foreground, the status of the foreground activity has to be recreated. The rotation of the screen finally causes the destruction of the current activity that must be redrawn with a new layout. A data loss problem occurs when data is accidentally deleted or state variables are accidentally assigned with 
default or initial values. Data loss faults can be the source of diverse failures .

***_DATA LOSS DETECTOR_***

+ Biased Model-Based Exploration

The test case generation strategy implemented in DLD consists in visiting as many states as possible and incrementally testing the newly discovered states to detect data loss faults. A too abstract representation would collapse many concrete states into a single abstract state causing several relevant states not being tested for data loss. A too concrete representation would cause an enormous waste of time, testing for data loss states with irrelevant differences. This is a waste of resources, because as long as some values are assigned to the various GUI elements, the data loss is likely to show up regardless of the concrete values assigned to these elements.
The test case generation strategy is biased towards the execution of new actions that may lead to new states potentially affected by data loss.

+	Data-Loss-Revealing Actions

To make sure the reached abstract state is fully tested for data loss, including the elements that might be outside the screen, if the check state step has not revealed a data loss, DLD executes a scroll down action that may make new elements appear. If this happens, a new abstract state might be reached, which would be again systematically tested for data loss. The fact that a podcast was loaded does not result in any visible difference in the timer window, and thus the abstraction strategy cannot capture the difference between the state that exposes the data loss fault and the one that does not. To address these cases, when an already visited state is encountered, DLD enables the probabilistic data-loss-revealing action that has the same probability of the other actions to be selected. {probabilistic data-loss-revealing action}. Data loss problems do not always cause crashes. DLD strategy is to collect the GUI state of the app before and after the execution of actions that may have triggered a data loss failure and compare the states to detect it.

+ Data Loss Oracles

Data loss problems do not always cause crashes. As anticipated in Section 3.2, the basicDLD strategy is to collect the GUI state of the app before and after the execution of actions that may have triggered a data loss failure and compare the states to detect it. Figure 2 shows the state information captured by the snapshot-based and the property-based oracles for a same GUI state of the OpenVPN app. The former oracle stores a screenshot of the app, as shown in Figure 2 , while the latter oracle stores the properties of the views in Python dictionary format, as shown in Figure 2 .
More rigorously, the two oracle strategies collect and compare state information as follows.

+ Snapshot-based oracle

Finally, DLD crops the header and the footer of the image because it contains information that changes over time regardless of data loss, such as the current time and the battery level. The resulting image is the retrieved representation of the current state.

+ Property-based oracle
The comparison fails if one of the attribute values is different or the hierarchical structure of the views is not preserved. Note that although the two strategies may seem redundant, they are not, as confirmed by our experiments. In particular, there are a number of data loss problems that can only be detected by one strategy. For instance, Figure 3 shows the case of a data loss failure that has been detected by the property-based oracle only.

__EVALUATION__

This section presents the empirical results obtained by experimenting DLD with a benchmark of 110 data loss faults, in comparison to the ALARic and Quantum test case generation techniques.

***Implementation***

We implemented DLD as an extension of DroidBot , which is a state-of-the-art test case generator for Android that does not implement features for the detection of data loss faults. As outcome of the testing process, DLD generates both a report with the revealed data loss faults and reproducible test cases. Each data loss is described in terms of the screenshots and the set of GUI properties collected before and after the data loss is observed.
Research Questions
1)	What is the ϵ that provides the best exploration?

This research question investigates the impact of the ϵ parameter on the effectiveness of the approach. To perform this initial study we selected 3 apps from the benchmark. We started with ϵ = 0, which consists of a strategy that always privileges the execution of actions that have not been executed before, based on the incrementally constructed GUI model. ϵ = 0.2, which produced a significant decrease on the effectiveness of the exploration.
2)	Is DLD more effective than state-of-the-art techniques?
This research question investigates the capability of DLD to reveal the data loss problems in the benchmark. To answer this research question, we manually analyzed every report produced by DLD to distinguish the actual data loss problems from the irrelevant spurious violations. We reproduced the problem in the unclear cases. For this research question, we detected data loss problems using both the snapshot-based and the property-based oracles.

We refer to the union of the benchmark and online data loss faults as the known data loss faults. We report the number of activities affected by a data loss problem found by DLD. They intuitively correspond to different faults and different fixes to be implemented in different activities. The only exception is with the known data loss faults.

Since some of the data loss faults in the benchmark affect the same activity, we actually report the precise number of faults in the benchmark that have been revealed. Finally, when only spurious violations are detected for an activity, we report it as a spurious data loss.

Table 2 column DLD shows the results that
Column Benchmark Data Loss avg /existing indicates the average and total number of data loss faults that have been revealed by DLD out of the ones present in the benchmark. For example in the BookCatalogue app, DLD revealed 6 data loss faults revealed across the three runs, out of a total of 7 data loss faults present in the benchmark. Data Loss avg /existing indicates the average and total number of data loss faults reported online revealed by DLD. Data Loss avg indicates the average and total number of previously unknown data loss faults revealed.

5 data loss faults of the benchmark on average, achieved a total of
Loss avg indicates the average and total number of activities that originated spurious violations only. Column Crashes reports the total number of activities that crashed due to data loss faults.
3)	What is the tradeoff between the snapshot- and property-based oracles?
We already discussed in Section 3.3 the qualitative differences between these two types of oracles, and reported examples of data loss faults that could be detected by one type of oracle only. Here, we assess quantitatively the impact of each class of oracles, on both the revealed data loss faults and the spurious oracle violations. Figure 6 shows the percentage of data loss faults detected and the number of spurious oracle violations produced by one-strategy only, either snapshot-based or property-based, or both of them. In the case of the spurious violations we have an additional category that is the violations caused by slow activity recreation after screen rotation, as anticipated in the Section discussing RQ1.
A small number of the spurious oracle violations is caused by a slow activity recreation, which causes the oracles to retrieve incorrect state information. In fact, only 0.1% of the spurious violations are produced uniquely by the property-based oracle, while 21.1% of the spurious violations are produced uniquely by the snapshot-based oracle. The largest proportion of the spurious violations are produced by both the strategies. Although the snapshot-based oracle produces more spurious violations than the property-based oracle, these violations seldom cause correct activities to be reported to the tester , thus it is relatively detrimental to use it in the testing process.
4)	Are data loss faults relevant to developers?
Finally, we investigated if data loss faults are relevant to app developers. DLD for 9 hours on each app and revealed 195 data loss faults that still affect these apps nowadays. We finally submitted a bug report online for each revealed data loss. This decision of course depends on the specific consequence of the data loss and the complexity of the activity that is affected by the fault. This also suggests that the definition of an automatic repair strategy that can address data loss faults could be extremely beneficial to improve the cost-effectiveness of the bug fixing process.

***Threats to Validity***

The main internal threats to validity about our study is the manual work done to identify the spurious violations among the data loss faults reported in the evaluation. The main external threats to validity concerns with the generalization of the results. The fact that we repeated the evaluation with the most recent versions of the apps revealing again many data loss faults is a further mitigation factor. 
While these approaches revealed several interesting faults in both open source and industrial applications , they are ineffective against data loss problems . In fact, they neither include operations that cause stop-start events nor they are equipped with oracles that can detect non-crashing data loss failures, which account for the majority of the failures as reported in our evaluation. The injected sequences concern with the audio service, the connectivity, and the lifecycle of the activities, which may reveal data loss faults. Similarly, when a user-generated model of the app under test is available, Quantum can generate tests that may reveal data loss, as reported in a small-scale evaluation.
ALARic is a mostly random test case generation technique that similarly to DLD exploits double screen rotations to reveal data loss faults. However, the biased exploration strategy, the enabledeness state abstraction, and the ad-hoc data-loss-revealing actions used by DLD outperformed ALARic in our evaluation. When the source code of the app is available, a static analysis technique such as KREfinder can be used to reveal data loss problems. On the contrary, the effectiveness of DLD does not depend on the complexity and size of the source code and seldom reports spurious data loss.
The neutral sequences of operations that DLD uses to reveal data loss problems can be seen as a specific class of metamorphic relations that relate executions with and without these sequences. Relations between executions, like the ones used in this paper to reveal data loss problems, have been also used to heal executions, for instance to produce automatic workarounds . While this approach might be exploited to prevent data loss failures, it also reduces the set of functionalities available to users. DataLossHealer is a healing solution designed to mitigate the impact of data loss faults in the field .
Although it might prevent some data loss faults, it has various drawbacks. For instance, it introduces overhead to save and restore data in presence of data loss faults, it can address only some data loss, and it requires rooting the device. DLD delivers a more effective solution revealing data loss faults upfront before the app is released.

***Related work***
While these approaches revealed several interesting faults in both open source and industrial applications , they are ineffective against data loss problems . In fact, they neither include operations that cause stop-start events nor they are equipped with oracles that can detect non-crashing data loss failures, which account for the majority of the failures as reported in our evaluation. However, the biased exploration strategy, the enabledeness state abstraction, and the ad-hoc data-loss-revealing actions used by DLD outperformed ALARic in our evaluation. When the source code of the app is available, a static analysis technique such as KREfinder can be used to reveal data loss problems. On the contrary, the effectiveness of DLD does not dependon the complexity and size of the source code and seldom reports spurious data loss.
While this approach might be exploited to prevent data loss failures, it also reduces the set of functionalities available to users. DataLossHealer is a healing solution designed to mitigate the impact of data loss faults in the field.

***_CONCLUSIONS_***

Android activity might be destroyed and later recreated. To avoid losing useful data during this process, apps must explicitly implement the logic necessary to save the data, when the activity is destroyed, and restore the saved data, when the activity is recreated. Unfortunately, this logic is often faulty. This paper presents Data Loss Detector, an automatic test case generation technique designed to reveal data loss faults.
DLD exploits an exploration strategy biased towards the discovery of new app states, data-loss-revealing actions, and two dedicated oracle-based strategies to automatically reveal data loss problems.
