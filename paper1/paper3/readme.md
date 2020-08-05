# A Dataset for GitHub Repository Deduplication

## Authors

+ Diomidis Spinellis
+ Zoe Kotti
+ Audris Mockus

***Conference Name:*** MSR-2020

***Introduction:*** Anyone can create a copy of a GitHub project through a single effortless click on the project’s fork button. Consequently, GitHub contains many millions of copied projects. The project details provided by the GitHub API contain the field fork, which is true for forked projects.

***Work methodology*** In the following sections we present how we created a dataset identifying and grouping together GitHub projects with shared ancestry or commits, the data schema and availability, an evaluation of data quality, indicative findings based on the dataset, related work, and ideas for research and improvements.

***Dataset Creation***

+ We first grouped shared commits to a single “attractor” project, which was derived based on the geometric mean (Table all project mean metric— 125 486 232 records—Listing 2) of six quality attributes:5 recency of the latest commit (Table most recent commit—100 366 312 records—Listing 3), as well as the number of stars (Table project stars—10 317 662 records— Listing 4), forks (Table project forks—6 958 551 records—Listing 5), commits (Table project ncommits—100 366 312 records—Listing 6), issues (Table project issues—9 498 704 records—Listing 7), and pull requests (Table project pull requests—7 143 570 records—Listing 8).
+ To cover holes in the coverage of shared commits, we complemented the projects sharing commits table with projects related by GitHub project forks, after removing a set of hand-picked and heuristic-derived projects that mistakenly linked together unrelated clusters (Table blacklisted projects— 2 341 896 records—Listing 10).
+ The final steps involved determining the size of each group (Table group size—2 472 758 records—Listing 12), associating it with each project (Table project group size—18 203 053 records—Listing 13) and its metrics (Table project metrics—18 203 053 records—Listing 14), obtaining the mean metric for the selected projects (Table project mean metric— 18 203 053 records—Listing 15), and associating with each group the project excelling in the metric (Table highest mean in group—7 553 705 records— Listing 16).
+ We used a query utilizing the SQL window functions in order to group together shared commits (Table projects sharing commits—44 380 204 records—Listing 9) without creating excessively large result sets (see Listing 16 in the appendix).

***Down the rabbit hole***

in GHTorrent shared commits do not always lead to the same ancestral commit, a query that exhausted 128GB of RAM, and a result set that exceeded component of copied projects would have a unique such ancestor, allowing the records of the project and commit identifier table by the commit identifier, to identify projects with common commits. The commit and project identifier table with the database’s dump utility, GB RAM) a set of projects sharing commits, thus reducing the amount of Our manual verification of large graph components uncovered a megacomponent of projects with 4 278 791 members.
edge-creation algorithm to include only projects sharing at least two commits.
could have drastic consequences, because only the top 60% of projects ordered by the number of recorded commits have more than two commits. one edges from projects with up to five edges. commits with 139 other projects.
This reduced considerably the mega-component size in the graph of projects with high-ranked projects in the same component involved genuine forks.
projects that were linking together unrelated repositories.
In some cases the culprits were high-ranked projects, such as boostorg/spirit, which links together more than ten Boost repositories,30 apache/hadoop, links to Reactive-Extensions/RxJS,32 ReactiveX/RxJava, which links several Netflix repositories,33 jashkenas/underscore, which links with lodash/lodash,34 jsbin/jsbin linking to cdnjs/cdnjs,35 ravendb/ravendb linking to SignalR/SignalR,36 Kibana linked with Grafana,37 CartoDB/carto linked with selected from the component one popular project with relatively few forks Some (very few) commits appear to be shared by an inordinate number of projects.
At the top, three commits are shared by 100 683 projects, However, these numbers are not necessarily wrong, because there are five projects with a correspondingly large number of forks: 125 491 (jtleek/datasharing), 124 326 The first two commits are associated with many (now defunct) projects of the user dvcsconnectortest (missingcommitsfixproof, missingcommitstest, and then missingcommitstest 250 1393252414399) for many different trailing numbers.

***Dataset overview***

The dataset is provided41 as two files identifying GitHub repositories using the login-name/project-name convention.
The file forks clones noise names is a 50 324 363 member superset of the source projects, containing also projects that were excluded from the mapping as noise.

***Duplication in Existing Datasets***

Since commits appear only in the history of the repositories they are pushed to, the activity in forked is independent from the activity in the associated base, so both types of repositories should be considered in the analyses of GitHub projects. Code duplication in GitHub was studied by Lopes et al. Project-level duplication includes appropriations that could be addressed by Git submodules, abandoned derivative development, forks with additional non-source code content, and unorthodox uses of GitHub, such as unpushed changes. Code duplication can hamper the statistical reasoning in random selections of projects, and skew the conclusions of studies performed on them, because the observations are not independent, and diversity may be compromised.
While it is common sense to select a sample that is representative of a population, the importance of diversity is often overlooked, yet as important . Especially in software engineering, where processes of empirical studies often depend on a large number of relevant context variables, general conclusions are difficult to extract .

***EVALUATION***

The two datasets share a substantial overlap both in terms of source projects and in terms of cluster leaders . On the other hand, it is clear that CDSC is considerably more comprehensive than CCFSC, covering an order of magnitude more repositories. G35 In 301 cases the clusters shared at least one common element. In general, we noticed that CDSC appears to be more precise than CCFSC at clustering, but worse at naming the clusters.
As an example of use of our dataset, we deduplicated the Reaper dataset , which contains scores concerning seven software engineering practices for about 1.8 million GitHub projects.
Since commits appear only in the history of the repositories they are pushed to, the activity in forked is independent from the activity in the associated base, so both types of repositories should be considered in the analyses of GitHub projects. Code duplication in GitHub was studied by Lopes et al. Project-level duplication includes appropriations that could be addressed by Git submodules, abandoned derivative development, forks with additional non-source code content, and unorthodox uses of GitHub, such as unpushed changes. Code duplication can hamper the statistical reasoning in random selections of projects, and skew the conclusions of studies performed on them, because the observations are not independent, and diversity may be compromised.

***A duplication issue was also identified by Irolla and Dey*** In the Drebin dataset , which is often used to assess the performance of malware detectors and classifiers . Half of the samples in the dataset have other duplicate repackaged versions of the same sequence of opcode. Similarly, Allamanis examined the adverse effects of code duplication in machine learning models of code . To resolve if deduplication of a dataset is needed, the true data distribution of the target use case should be first interpreted.

 ***_RESEARCH AND IMPROVEMENT IDEAS_***

In addition, the dataset can be used for investigating the ecosystem of duplicated projects in terms of activity, duplication methods , tree depth, currency, or trustworthiness.

***ABSTRACT***

We provide a dataset of 10.6 million GitHub projects that are copies of others, and link each record with the project’s ultimate parent. The ultimate parents were derived from a ranking along six metrics. The related projects were calculated as the connected components of an 18.2 million node and 12 million edge denoised graph created by directing edges to ultimate parents. The graph was created by filtering out more than 30 hand-picked and 2.3 million pattern-matched clumping projects.

An evaluation of our dataset against another created independently with different methods found a significant overlap, but also differences attributed to the operational definition of what projects are considered as related.

