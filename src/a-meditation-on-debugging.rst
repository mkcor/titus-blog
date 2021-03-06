A (Short) Meditation on Debugging
#################################

:author: C\. Titus Brown
:tags: python,testing
:date: 2007-05-29
:slug: a-meditation-on-debugging
:category: python


I spent part of Saturday and Sunday working on Cartwheel, and then I
spent part of Monday morning nailing down a bug that I thought I'd
introduced.  The process of tracking down and fixing this bug led me
to give serious thanks for version control and automated tests, and
at last gave me a nice compact story to tell when urging scientists
to use version control.

(I doubt anyone reading this needs encouragement to use VCS (although
I'd bet that not everyone tests like they should; I certainly don't!)
but it does serve as a good cautionary tale.)

Briefly, I had introduced a bunch of new logic to allow parsing and
exporting of results from within the Cartwheel Web site itself.  This
led to increased complexity in the Web site, of course, but I'd written
automated functional tests along with the new code, and everything was
working.

...at least, everything was working until I ran *all* of the
functional tests, not just the ones immediately relevant to my code.
After a serious amount of effort (ref note 0), I discovered that a
section C test failed if (and only if): ::

    (any three of four section A tests were enabled) AND (a particular section B test was enabled)

Now, this was puzzling, because section A, section B and section C
were almost entirely decoupled (ref note 1).

I gamely dove in and started disabling various parts of the various
tests (ref note 2).  By focusing on the simplest tests (ref note 3) 
I quickly discovered that any database reference led to the error, and
this led me instantly to the database caching layer (ref note 4).

OK, so everyone has gone through this, right?  Why was this special for me?

Note 0 -- because my tests were automated, I could replicate the fault
on demand, which meant that I could eventually figure out exactly what
tests had this bad interaction.  Try that without automation!

Note 1 -- experienced developers will immediately recognize the
presence of epistatic interactions between modules in test faults as a
sign that you need to take a close look at whatever layer is in common
between the modules.  I, for some reason, did not.  *Note to self:
remember this.*

Note 2 -- try systematically disabling (and re-enabling) portions of your
code without version control.  You will quickly fall into a suicidal state
and end up with large portions of your application disabled because you
forgot what you did.

Note 3 -- focusing on deconstructing the simplest tests seems obvious
in hindsight, but it wasn't at the time.  *Note to self: remember
this.*

Note 4 -- see note 1.  Why did it take me so long to get here?  Also
note that because of the level of the problems, it's extremely
unlikely that any unit tests would have caught this; huzzah for
functional tests!

In hindsight, then, this problem was mainly special because I handled
it so obtusely ;).  I had the advantage of an automated test suite,
full knowledge of all the source code and architecture, full version
control, and almost two decades of experience in programming, and it
still took me about 6 straight hours to track this bug down.  I don't
know how people without this infrastructure manage, and I certainly
don't know if I would have even *found* it without the test suite;
there's no indication that it was causing problems with the site yet,
but it *would* have if website load increased by only a little bit.

So, use version control & write tests, everyone!

For those of who that have come this far, here's a little treat from
the testing-in-python list: Kumar McMillan `gives the best description
of the difference between unit tests and functional tests that I've
seen <http://lists.idyll.org/pipermail/testing-in-python/2007-April/000265.html>`__.

Peace out,

--titus
