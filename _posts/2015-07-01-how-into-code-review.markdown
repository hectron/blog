---
layout:     post
title:      How into Code Review
date:       2015-07-02 12:00:00
summary:    So you started code reviewing -- great. Let's make those code reviews effective.
---

## TL; DR

Context is king. Be specific about what your code is doing and _why_
it's the way that it is.

Don't be a chump when you review someone else's code. Find what you like
about the code review and comment on it. Find something you don't like?
Question it nicely.

Code reviews are about sharing and learning.

----------

## A little background

When I started working at my current job, I was overwhelmed. The
applications that we had were massive, monolithic applications that were
designed surprisingly well.

It may have been to due the actual visibility of code online, but I
started getting concerned about the code that was being merged in. I
pestered my manager to allow me to pair program or code review with some
developers, if only for just an hour a week. My manager was all for it,
but no other developer wanted to pair with me.

After several months of trying, I kept bringing it up to my manager and
we decided that perhaps we should implement code reviews via Pull
Requests.

## The theory of Pull Requests

In theory, pull requests should be a place where intelligent
conversation is had regarding code that is to be merged. They should be
reviewed, accepted and merged for the code to actually go out. It should
have many pairs of eyes looking at it to try to see what consequences it
will have.

This is all great if you have a team that actively reviews each other's
code. The best way to go about implementing a strong code review culture
is to **lead by example**.

## Code Reviews 201

### Preparing to ask for a review

I like to write up my code review request before asking someone to
review my code. The total write up is about 3-5 paragraphs. The write up
contains about three sections.

The first section provided is titled "context" in which the context for
the work is explained. This explains explains the business value of why
the work was needed.

The next section is titled "cause." It explains why the previous code
was doing what it was. If it's a new feature, explain why the old
features were just not cutting it. This is usually clear by the time the
code is ready.

The last section is titled "solution." This is where one **succinctly**
explains the work done and what it hopes to accomplish.

### Asking for a code review

Once the write-up is ready, either copy your code into a code-sharing
tool like [Gist](https://gist.github.com/),
[JsFiddle](http://jsfiddle.net/), [Stypi](https://code.stypi.com/), or
open a pull request. If you're not going to merge it in, label it as so.

Find a co-worker, colleague, friend, or an online coding website. 
**Kindly and briefly** ask for a code review if they have time. Provide
them with the short summary of the code in question, and _give them a
clear date for when you'd expect the code to be reviewed_.

The last point is critical: if the code is needed to be reviewed for a
same-day release, you'll want to find someone who will take time out of
their day to help you out.

### Reviewing someone else's code

There are three rules I abide by.

- Don't be a chump.
- Provide useful, timely feedback.
- Don't be a chump.

If someone asked you to review their code, they want it to be critiqued
and improved. This does not give the code reviewer a pass to be a chump.

The first thing I do is I **really try to** find things about the code
that I like.  When a code review has some questionable code, simply
question it. It's better to improve code by questioning it rather than
insulting the author.

If you find something that could be better, phrase your findings such
that they form a question. This will lesson the negativity resulting
from identifying spotty code.

Be courteous and ask when they expect feedback by. As mentioned above,
sometimes a review is critical and you might not have time to review it.
That's OK. They'll understand.

Lastly, remember to be positive. The purpose of code reviews is to share
knowledge and improve the quality of the base code. Work together toward
that goal and not against each other to prove who can code better.


## Final notes

I think code reviews and/or pull requests should be a part of everyone's
work flow. Paired with intelligent conversation, they truly improve the
quality of the code base.

If you ask for a code review, I challenge you to lead by example by:

- Writing at least 3 paragraphs explaining your change.
- Doing it frequently so that they can be easily reviewed.
- Be kind when asking for a code review.

If you are a person reviewing someone else's code, I challenge you to:

- Drop your ego while reviewing code.
- Be timely and helpful in your reviews.
- Ask positive questions when you find bad code.

