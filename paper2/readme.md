# Data Loss Detector: Automatically Revealing Data Loss Bugs in Android Apps

## authors

+ Oliviero Riganelli
+ Simone Paolo Mottadelli
+ Claudio Rota
+ Daniela Micucci
+ Leonardo Mariani

***Conference Name:*** ISSTA ’20

***Introduction:*** Data loss faults may affect the correctness of the apps in many different ways. Data loss faults can be extremely pervasive. Considered the execution of system events jointly with test suites and reported that all the four apps used in their evaluation were affected by data loss faults. Test case generation techniques could be potentially used to reveal data loss faults.

Some techniques have been designed to extend the fault discovery capability of existing test suites to data loss problems. ALARic can successfully reveal data loss faults, but the adopted exploration strategy and oracles have limited effectiveness, as reported in our evaluation. In this paper, we present Data Loss Detector , an automatic testing technique that can reveal data loss problems in Android apps. Finally, the biased model-based exploration and the data-loss-revealing actions exploited in DLD allow a more effective data loss detection than the strategy implemented in Alaric .

, which includes 110 data loss problems affecting 54 app releases. DLD automatically detected 83 of the 110 data loss problems. DLD also revealed 35 data loss faults that were not part of the benchmark, but were reported online in bug reports, and 232 previously unknown data loss faults. Overall DLD revealed three times the data loss faults revealed by competing approaches.

We finally submitted the data loss faults that still affect apps nowadays online to app developers who positively reacted to our bug reports. Section 3 describes the main technical contributions of this paper, including the biased model-based exploration strategy, the data-loss-revealing actions, and the automatic oracles.

