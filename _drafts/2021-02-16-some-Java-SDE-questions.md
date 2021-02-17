---
published: false
---
**Certificates/networking/SSL**
How does HTTPS work for internet-facing browser applications?
How do we configure 2-way SSL? In Java applications?
In more details how handshake works on packets level

**Java 8**
Difference between ArrayList & LinkedList?
How is HashMap implemented? TreeMap?
Having Stream.of("hello", "world").map(a -> { System.out.println(a); return a; }) code, what will it print when executed in public static void main? (A: nothing because termination operator is missing)
What interface is expected for .filter method in Optional & Stream?
When would you use LocalDateTime & when Instant? What is their representation acc. to ISO 8601?

**Design Patterns**
Why do we need the pattern languages of software design?
Describe the pattern you like the most or find very useful? (would be cool if Observer)
Implement it (interviewer pays close attention) & describe when it's best suited and when less suited (maybe a situation when simple and flexible). What common mistakes people make when implementing this design pattern?
In the book of Gang of Four they describe some popular patterns, are you familiar? how did they group them logically?

**Spring Boot**
Why was dependency injection invented? How is inversion of control beneficial? Coupling vs. cohesion?
What annotations do you know? Describe when they're used and how?
What is Spring Boot? How will you implement a new library that adds general capability to all your Spring apps? (spring boot starter is a soundable option)

**REST API**
In a form below describe endpoints to create new customers, update existing ones, get list of books assigned to the customer.
{Method} {Path including query params}
{Request headers}
{Request body}

{Status code}
{Response headers}
{Response body}

Richardson maturity model, also known as Towards the Glory of REST.

**TDD/Unit testing**
What is TDD? What is unit in unit testing? (https://tanzu.vmware.com/content/blog/what-is-a-unit-test-the-answer-might-surprise-you)
Difference between Spy, Fake, Stub and Mock.
Test Pyramid

**Concurrency**
Synchronized blocks vs locks
Atomic counters and how they're implemented?
ConcurrentHashMap implementation?
Difference between Semaphore & ReentrantLock? When can you use what?
How do JVM threads map on OS threads?
Implement thread-safe LRU cache

**Reactive programming**
What is it? When should we consider it? (A1: when crazy amount of I/O is going on, many blocked threads become expensive (in current version of Java), A2: when batches need to be controlled by the receiving side, back-pressure capability)
What will this code execute in psvm Flux.just("hello", "world").map(a -> {​ System.out.println(a); return a; }​) ? (A: nothing, nobody subscribed to the Publisher)
How do we split publisher a by a property into two fluxes? (A: convert to some hot publisher and then filter)

**NoSQL/MongoDB**
Why do we need them? (A: more optimally solve specific problems in network partition tolerant environments)
How do we design schema in schema-on-write databases like MongoDB? (A: we think about how it's going to be used, don't strive to normalize it when performance is hit)