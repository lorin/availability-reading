# Availability reading list

This page contains references to paper and books about building
highly available systems.

The focus here is on practical information for building systems. It doesn't
cover theoretical topics such as distributed algorithms, nor does it cover
distributed databases, so don't expect to see the Paxos or Dynamo papers here.

I also maintain a [systems and failure reading list][1], which
covers systems and failure at a higher-level.

Mark McGranaghan maintains a [services engineering reading list][2] with some
significant overlap.



[1]: https://github.com/lorin/systems-reading
[2]: https://github.com/mmcgrana/services-engineering

### Why Do Computers Stop and What Can Be Done About It?
Jim Gray,
Tandem Computers,
Technical Report 85.7
June 1985,
PN87614

[pdf][gray85]

Describes strategies for achieving good reliability and availability in the
presence of faults.

Notable quotes:

* System administration, which includes operator actions, system configuration, and system maintenace was the main source of failures -- 42%. p8

* The top priority for improving system availability is to reduce administrative mistakes by making self-configured systems with minimal maintenance and minimal operator interaction. p12

* A way to improve availability is to install proven hardware and software, and then leave it alone. p13

* If you consider an industrial sofwtare system which has gone through structured
design, design reviews, quality assurance, alpha test, beta test, and months or
years of production, then most of the "hard" software bugs, ones that always
fail on retry, are gone. *The residual bugs are rare cases, typically related to
strange hardware conditions (rare or transient device fault), limit conditions
(out of storage, counter overflow, lost interrupt, etc,, or race conditions
(forgetting to request a semaphore)*.  p17-18 (emphasis mine).

* Dealing with system configuration, operations, and maintenance remains an unsolved problem. p32

### Making Reliable Distributed Systems In The Presence Of Software Errors
Joe Armstrong,
PhD Dissertation,
Royal Institute of Technology,
Stockholm, Sweden
Decmeber, 2003

[pdf][armstrong03]


Describes both Erlang and principles for using it to build reliable systems.

### Release It!: Design and Deploy Production-Ready Software
Michael Nygard,
Pragmatic Bookshelf,
April, 2007

### On Designing and Deploying Internet-Scale Services
James Hamilton,
Proceedings of the 21st Large Installation System
Administration Conference (LISA '07),
November 11-16, 2007

[html][hamilton07]

Even though this paper was written before cloud computing became widely adopted
(the word "cloud" does not appear once), it feels as if it could have been
written today. The only other indications of it being a little are a discussion
of hardware, and a proposed deployment cycle of three months.

### Web Operations: Keeping the Data on Time
John Allspaw & Jesse Robins, eds.
O'Reilly Media,
July 2010

A collection of essays.


### Simple Testing Can Prevent Most Critical Failures: An Analysis of Production Failures in Distributed Data-Intensive Systems

Ding Yuan, Yu Luo, Xin Zhuang, Guilherme Renna Rodrigues, Xu Zhao, Yongle
Zhang, Pranay U. Jain, and Michael Stumm
Proceedings of the 11th USENIX Symposium on Operating  Systems Design and Implementation (OSDI '14)
Oct. 2014.

[pdf][yuan14]

An empirical study that explores the reasons why distributed systems
fail in production by analyzing the root causes of around 200 confirmed system
failures. You can read [my review](http://neverworkintheory.org/2014/10/08/simple-testing-can-prevent-most-critical-failures.html) of this paper at *It Will Never Work In Theory*.

### Notes on Distributed Systems for Youngbloods
Jeff Hodges,
Something Similar blog,
January 14, 2013

[html][hodges13]

General advice from a Twitter engineer about the challenges of developing and
debugging distributed systems. He also gave an excellent talk at RICON West 2013
entitled [Practicalities of Productionizing Distributed Systems][hodges13-talk]
that is well worth your time.


### Fault Injection in Production: Making the case for resiliency testing
John Allspaw,
ACM Queue, Volume 10, issue 8
August 24, 2012

[html][allspaw12]

Allspaw argues that you must observe the system tolerating failures in
production in order to have confidence in the system's resiliency. He discusses
fault injection in the context of GameDay exercises at Etsy. Although the essay
does not mention Chaos Monkey, it provides a strong motivation for tools similar
to Chaos Monkey.


[gray85]: http://www.hpl.hp.com/techreports/tandem/TR-85.7.pdf
[armstrong03]: http://www.erlang.org/download/armstrong_thesis_2003.pdf
[hamilton07]: https://www.usenix.org/legacy/event/lisa07/tech/full_papers/hamilton/hamilton_html/
[yuan14]: https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-yuan.pdf
[hodges13]: http://www.somethingsimilar.com/2013/01/14/notes-on-distributed-systems-for-young-bloods/
[hodges13-talk]: https://www.youtube.com/watch?v=BKqgGpAOv1w
[allspaw12]: http://queue.acm.org/detail.cfm?id=2353017
