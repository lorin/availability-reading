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
ACM Queue, Volume 10, issue 8,
August 24, 2012

[html][allspaw12]

Allspaw argues that you must observe the system tolerating failures in
production in order to have confidence in the system's resiliency. He discusses
fault injection in the context of GameDay exercises at Etsy. Although the essay
does not mention Chaos Monkey, it provides a strong motivation for tools similar
to Chaos Monkey.

### The Error Model
Joe Duffy,
Joe Duffy's Blog,
February 7, 2016

[html][duffy16]

Duffy talks about the error model that they used in the
[Midori](http://joeduffyblog.com/2015/11/03/blogging-about-midori/) language.
Interesting content about how to handle errors in code.

### A New Accident Model for Engineering Safer Systems
Nancy Leveson,
Safety Science, Vol. 42, No. 4, April 2004

[pdf][leveson04]

Leveson proposes a model of accidents called STAMP: systems-theoretic accident
model and processes. STAMP focuses on identifying safety constraints that were
violated and determining why the controls were inadequate.

While this paper is focused on software safety, it is still relevant for
availabilty, since an outage can be viewed as an accident.

### Why do Internet services fail, and what can be done about it?
David Oppenheimer, Archana Ganapathi, and David A. Patterson,
4th Usenix Symposium on Internet Technologies and Systems (USITS ‘03), 2003.

[pdf][oppenheimer03]

Oppenheimer et al. did a case study of three Internet services to determine
common causes of failures. Findings incldue:

* Front-end machines are a significant source of failure, largely due to operator
  configuration errors.
* Operator error is the leading cause of service failure in two of the three services.
* Operator error was generally due to misconfiguration rather than procedural
  errors.
* Operator error generally arose when operators were making changes to the system.
* Networking problems were a significant cause of failure.

Networking problems are difficult to mask because:

* networks are often a single point of failure
* network failure modes tend to be complex

Proposed techniques for avoiding or mitigating failures, in decreasing order of
impact:

 * Online correctness testing
 * Thoroughly expose and monitor for software and hardware failures
 * Redundancy
 * Config. checking
 * Online fault/load injection
 * Component isolation
 * Pre-deployment fault/load injection
 * Proactive restart
 * Pre-deployment correctness testing

### I want to believe: some myths about the management of industry safety
Denis Besnard, Erik Hollnagel,
Cognition, Technology and Work, Springer Verlag, 2014, 16 (1)

[pdf][besnard14]

The authors discuss five myths about safety and propose revisions.

#### Human error

Myth: Human error is the largest single cause of accidents and incidents

Revision: 'Human error' is an artifact of a traditional engineering view, which
treats humans as if they were (falliable) machines and overlooks how performance
adjustments are used to match activities to the working conditions.

#### Procedure compliance

Myth: Systems will be safe if people comply with the proedures
they have been given.

Revision: Actual working situations usually differ from what the procedures
assume and strict compliance may be detrimental to both safety and efficinecy.
Procedures should be used carefully and intelligently.

#### Protection and safety

Myth: Safety can be improved by barriers and protection;
increasing the layers of protection leads to higher safety.

Revision: Technology is not value netural. Additional prteoction changes
behaviour so that the intended safety improvements might not be obtained.

#### Mishaps and root causes

Myth: Root cause analysis can identify why mishaps happen
in complex socio-technical systems.

Revision: Human performance cannot be described as if it was bimodal. In
socio-technical systems, things that go wrong happen in the same way as things
that go right.

#### Accident investigation

Myth: Accident investigation is the logical and rational
identification of causes based on facts.

Revision: Accident investigation is a social process, where causes aer
constructed rather than found.

#### Safety first

Myth: Safety always has the highest priority and will never be
compromised.

Revision: Safety will be as high as affordable — from a financial and ethical
perspective.

## Hints for Computer System Design
Butler W. Lampson,
ACM SIGOPS Operating Systems Review,
Volume 17 Issue 5, October 1983

[pdf][lampson83]

General advice on building system, based on the author's experiences building
several systems at Xerox PARC. It's all still relevant, but here are some
quotes I found particularly notable:

Defining interfaces is the most important part of system design.

Interface design must satisfy three conflicting requirements:

1. An interface should be simple
2. An interface should be complete
3. An interface sould admit a sufficiently small and fast implementation

Do one thing at a time, and do it well.

Don't generalize; generalizations are generally wrong.

Neither abstraction nor simplicity is a substitute for getting it right.

The purpose of abstractions is to conceal *undesirable* properties; desirable
ones should not be hidden.

*Use procedure arguments* to provide flexibility in an interface (support
functions as arguments).

Keep basic interfaces stable.

Even when an implementation is successful, it pays to revisit old decisions as
the system evolves; in particular, optimizations for particular properties of
the load or the environment (memory size, for example) often come to be far
from optimal.

*Use a good idea again* instead of generalizing it.

Handle normal and worst cases separately as a rule.

In allocating resources, strive to avoid disaster rather than to attain an
optimum.

We learned that the only important thing is to avoid thrashing.

The most successful schemes give a fixed share of the cycles to each job and
don't allocate more than 100%.

Shed load to control demand, rather than allowing the system to become overloaded

End-to-end: Error recovery at the application level is absolutely necessary for a reliable
system, and any other error detection or recovery is not logically necessary
but is strictly for performance.

Two problems with the end-to-end strategy:

1. It requires a cheap test for success
2. It can lead to working sytems with severe performance defects that may not
   appear until the system behcomes operational and is placed under heavy load.

Log updates to record the truth about the state of an object.

[gray85]: http://www.hpl.hp.com/techreports/tandem/TR-85.7.pdf
[armstrong03]: http://www.erlang.org/download/armstrong_thesis_2003.pdf
[hamilton07]: https://www.usenix.org/legacy/event/lisa07/tech/full_papers/hamilton/hamilton_html/
[yuan14]: https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-yuan.pdf
[hodges13]: http://www.somethingsimilar.com/2013/01/14/notes-on-distributed-systems-for-young-bloods/
[hodges13-talk]: https://www.youtube.com/watch?v=BKqgGpAOv1w
[allspaw12]: http://queue.acm.org/detail.cfm?id=2353017
[duffy16]: http://joeduffyblog.com/2016/02/07/the-error-model/
[leveson04]: http://sunnyday.mit.edu/accidents/safetyscience-single.pdf
[oppenheimer03]: http://roc.cs.berkeley.edu/papers/usits03.pdf
[besnard14]: https://hal-mines-paristech.archives-ouvertes.fr/hal-00720270
[lampson83]: https://www.microsoft.com/en-us/research/publication/hints-for-computer-system-design/
