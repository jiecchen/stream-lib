## Description


A Java library for summarizing data in streams for which it is
infeasible to store all events. More specifically, there are classes
for estimating: cardinality (i.e. counting things); set membership;
top-k elements and frequency.  One particularly useful feature is that
cardinality estimators with compatible configurations may be safely
merged.

These classes may be used directly in a JVM project or with the
provided shell scripts and good old Unix IO redirection.

The ideas here are not original to us. We have endeavored to create
useful implementations from iterating over the existing academic
literature.  As such this library relies heavily on the work of
others.  Please read the [Sources](#Sources) and
[Reference](#References) sections.

## Examples

    $ echo -e "foo\nfoo\nbar" | ./bin/topk 
    item count error
    ---- ----- -----
     foo     2     0
     bar     1     0
    
    Item count: 3

    
    $ echo -e "foo\nfoo\nbar" | ./bin/cardinality 
    Item Count Cardinality Estimate
    ---------- --------------------
             3                    2


## Building

Assuming you have [Apache Maven](http://maven.apache.org/) installed
and configured:

    mvn package
   
And you should be all set.

## Where People Hang Out

Mailing list: http://groups.google.com/group/stream-lib-user


## Sources

The set membership code is the Bloom Filter implementation from Apache
Cassandra circa December 2009.  The changes here are minimal and were
for the purpose of testing and independent use. Apache Software
Foundation headers have been retained on these files.  By extension we
also include [murmurhash](http://murmurhash.googlepages.com/).

We were inspired to use this code by Jonathan Ellis' post
[All you ever wanted to know about writing bloom filters](http://spyced.blogspot.com/2009/01/all-you-ever-wanted-to-know-about.html).

## References

There are javadoc references to specific papers.  These were the ones
we found most relevant during out research.

#### Cardinality

 * Min Cai, Jianping Pan, Yu K. Kwok, and Kai Hwang. Fast and accurate
traffic matrix measurement using adaptive cardinality counting. In
MineNet ’05: Proceedings of the 2005 ACM SIGCOMM workshop on
Mining network data, pages 205–206, New York, NY, USA, 2005. ACM.

 * Ahmed Metwally, Divyakant Agrawal, and Amr E. Abbadi. Why go
logarithmic if we can go linear?: Towards effective distinct counting of
search traffic. In EDBT ’08: Proceedings of the 11th international
conference on Extending database technology, pages 618–629, New York,
NY, USA, 2008. ACM.

 * Nikos Ntarmos, Peter Triantafillou, and Gerhard Weikum. Counting at
large: Efficient cardinality estimation in Internet-Scale data networks.
In ICDE ’06: Proceedings of the 22nd International Conference on Data
Engineering, pages 40+, Washington, DC, USA, 2006. IEEE Computer
Society.

 * Marianne Durand and Philippe Flajolet. LogLog counting of large
cardinalities. In ESA03, volume 2832 of LNCS, pages 605–617, 2003.

 * Kyu Y. Whang, Brad T. Vander Zanden, and Howard M. Taylor. A
linear-time probabilistic counting algorithm for database applications.
ACM Trans. Database Syst., 15(2):208–229, 1990.

 * Moses Charikar, Kevin Chen, and Martin F. Colton. Finding frequent
items in data streams. In ICALP ’02: Proceedings of the 29th
International Colloquium on Automata, Languages and Programming,
pages 693–703, London, UK, 2002. Springer-Verlag.

 * Stefan Heule, Marc Nunkesser, Alex Hall.  HyperLogLog in Practice: 
Algorithmic Engineering of a State of The Art Cardinality Estimation 
Algorithm.  Proceedings of the EDBT 2013 Conference, ACM, Genoa, Italy 


#### Top-K

 * Graham Cormode and S. Muthukrishnan. An improved data stream
summary: The Count-Min sketch and its applications. pages 29–38.
2004. 10.1016/j.jalgor.2003.12.001
http://dl.acm.org/citation.cfm?id=1073718

 * Cheqing Jin, Weining Qian, Chaofeng Sha, Jeffrey X. Yu, and Aoying
Zhou. Dynamically maintaining frequent items over a data stream. In
CIKM ’03: Proceedings of the twelfth international conference on
Information and knowledge management, pages 287–294, New York,
NY, USA, 2003. ACM. 10.1145/956863.956918
http://dl.acm.org/citation.cfm?id=956918

 * Ahmed Metwally, Divyakant Agrawal, and Amr Abbadi. Efficient
computation of frequent and top-k elements in data streams. pages
398–412. 2005. 10.1007/978-3-540-30570-5_27
http://link.springer.com/chapter/10.1007/978-3-540-30570-5_27

#### Frequency

 * Graham Cormode and S. Muthukrishnan. An improved data stream
summary: The Count-Min sketch and its applications. 2004. 10.1016/j.jalgor.2003.12.001
http://dl.acm.org/citation.cfm?id=1073718

