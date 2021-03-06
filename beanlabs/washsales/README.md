# Scripts to Handle Wash Sales

This is a set of scripts and plugins which I use to identify and mark stock
sales that are to be washed according to the rules set by the IRS. There are two
problems which can be apparent in this code:

1. The rules themselves are complex and result in ambiguous cases. I've spent a
   significant amount of time trying to understand all their implications and it
   turns out that there are cases which are unclear. Other people have attempted
   to code these into a set of rules as well, e.g.,
   https://github.com/bbreslauer/wash-sale-tracker. What I support here is the
   manual identification of which lots are to be washed.

2. The other problem is that Beancount's default branch [as of May 2016] does
   not carry acquisition dates in its lots. So I've had to apply some ugly
   kludge in the 'carry_date_and_book_cost' branch in order to make this work in
   the meantime. The 'booking' branch will solve this problem entirely.


Update [2016-08-21]:

Beancount now supports dated postings by using the new booking algorithm, which
can be enabled like this:

  option "booking_method" "FIFO"

It's likely that by the time you're reading this, this method will have become
the default booking method.
