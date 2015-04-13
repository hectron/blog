---
layout:     post
title:      Delaying a front-end hotfix
date:       2015-04-12 21:13:00
summary:    A hot-fix was going to take place for a front-end intranet application until we found a hacky patch.
---

## TL; DR

This was done in Chrome by adding a "page" bookmark, and pasted the following
into the URL of the bookmark:

`javascript:jQuery('.currency-options').toggle();`

Whenever the end user would not be able to see the section, they simply click
the new bookmark and the section would show up.

----------

## A little background

There was an error in one of our applications recently. The error involved a
section in the DOM that was not displaying to the end user (but it _was_ in the
DOM). 

I suspect that this error was the result of hot-fixing every day of our two week
sprint. Let that sit.

> We hot-fixed every day in our two week sprint.

The team's morale was at an all-time low and we decided to bite the bullet and
just take two days to prep an actual release. During the time we were preparing
the release, a critical issue came in. Intranet users were unable to see a
currency box that is critical.

## Finding out the problem

The very first thing I did was I verified the issue for multiple users. Then I
inspected the area of the front-end application where the content was missing.

What happened was that there was bad data parsing being done on the app, and a
callback was never being fired. The callback simply performed a
`jQuery.toggle()` with the data that was being parsed.

jQuery specifies that the `toggle()` method simply `Use true to show the element
or false to hide it.` Therefore all we needed to do is somehow call toggle on
that element whenever a user tried to view it.

## Sometimes you gotta patch

Since we were on track to make a release, we had to make a decision. Either
involve a whole team and schedule a deploy to take place later in the evening,
avoid fixing the issue (not really an option) or find a work around.

Rather than starting another multi-hour hot-fix that would involve coding a
solution, updating integration tests to verify the solution, and have a QA team
perform a regression test, I ended up coding a JavaScript function, saved it as
a bookmark, and gave the bookmark to the main intranet users.

## Why use the bookmark approach?

We were already breaking many rules in proper, ethical, and respectable
development. Luckily, we **only support the latest version of Google Chrome on
_Mac_**. Having only to worry about fixing this on one browser was a blessing.

The code I ended up writing was this:

`javascript:jQuery('.currency-options').toggle();`

We packaged that up into a bookmark for users to have in their Chrome bookmarks
toolbar, and before you knew it, all of our users who did not have access to
those fields were now pleased to be able to check out and edit their values.

## Final notes

If you're reading this blog, then you know that I try to follow standard
procedures but often have to deviate from them in order to accomplish something. 

Unfortunately, we were in a position where we didn't want to modify production
code, but wanted to get a temporary fix our as soon as possible. This
work-around worked just fine and it gave us enough breathing room to make a
(significant) release.
