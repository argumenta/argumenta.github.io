---
layout: post
---

## Open Alpha

A little bit ago, [Argumenta.io][Argumenta.io] was launched as an open
alpha. Since then, a few people have expressed interest in learning more
about both its background and the design of [Argumenta][Argumenta], the
software behind it. I've been meaning to write an introductory post for a
while, so now seems like a good time!

## Social Argument Collaboration

[Argumenta.io][Argumenta.io] is a new site for social argument
collaboration.  Our goal is to provide a place for people to focus on
building better arguments online, while connecting with others who
share both similar and differing perspectives.

<a href="/assets/images/Argumenta-0.1.4.png">
  <img class="post-image" src="/assets/images/Argumenta-0.1.4.png">
</a>
<div class="post-caption">
  The home page for Argumenta.io
  (<a href="https://argumenta.io">https://argumenta.io</a>)
</div>

By "better" arguments, we envision ones that are more focused in their
presentation, diverse in their contents, and impactful in their effect;
supported and disputed more directly; and analyzed more thoughtfully.

Here's the essentials:

+ Arguments are built from propositions - a series of premises and a conclusion.
+ Propositions are short, tweet-like strings of text - 240 characters max.
+ Both are identified by the SHA-1 hash of their object record, just as in Git.
+ Support and Dispute tags link a proposition with a related argument.
+ Citation tags link propositions with any external resource (text, video, URLs).
+ Discussions allow for friendly analysis of each argument as a whole.

## Argument Publishing

As an environment focused on crafting arguments of high quality,
Argumenta also provides a place where people can publish their
resulting work. Each user receives a profile page with a timeline of
their most recent publications. Any arguments, propositions, or other
content that you publish will appear here.

<a href="/assets/images/Argumenta-0.1.4-profile.png">
  <img class="post-image" src="/assets/images/Argumenta-0.1.4-profile.png">
</a>

<div class="post-caption">
An example profile page
(<a href="https://argumenta.io/qualiabyte">https://argumenta.io/qualiabyte</a>)
</div>

In the future, we plan to add a "Follow" feature (à la Twitter) so
that you can follow the users who you respect or simply find
interesting, and then stay up to date with their latest arguments in a
merged personal timeline.

## Argumenta Objects

When you create an argument in Argumenta, you provide three things: a
title, a series of premises, and a conclusion. The server creates a
Proposition object for each premise and conclusion, and an Argument
object that points to these. Each object has its own object record,
and the record's SHA-1 hash identifies the object.

<a href="/assets/images/argumenta-objects.png">
  <img class="post-image" src="/assets/images/argumenta-objects.png">
</a>
<div class="post-caption">Argumenta Objects</div>

A Commit object is also created to record who published the argument,
where it was published, and when. A Repo points to the latest commit,
making the most recent version of each Argument easily human-accessible
by username and title. Support, Dispute, and Citation tags link
propositions with other resources &ndash; and are also objects with
their own record, commit, and SHA-1.

<a href="/assets/images/object-records.png">
  <img class="post-image" src="/assets/images/object-records.png">
</a>
<div class="post-caption">Object Records</div>

The above diagram illustrates Argumenta's object record format, which
is very much inspired by Git. Since we're still in alpha, it's
conceivable that the format may change slightly in the future &ndash; but we
do aim for stability, making any changes backwards-compatible when
possible. See the [code][Argument-Records] for more details!

## Argumenta Widgets

[Argumenta Widgets][Argumenta-Widgets] is a collection of components
using HTML, CSS, and JavaScript to display Argumenta resources in the
browser. Available widgets include Users, Arguments, Propositions,
Tags, and Discussions.  We use these to power Argumenta itself &mdash;
and you can embed them on any site supporting HTML5!

Here's an example Argument widget:

<div class="argument-widget" data-repo="qualiabyte/the-value-of-bitcoin-for-the-99%">
</div>

The Argument widget is quite interactive, and showcases the other
widgets as subcomponents. You can click on an argument's top panel to
toggle its contents, and click any proposition to reveal its tags. By
doing so, you can "drill-down" into the reasoning for or against any
item.

When an argument is displayed in the browser, its repo, SHA-1, and other
object data is passed to an Argument widget by HTML5 data attributes
(or API queries, if necessary), which renders the argument.

Here's the minimal code for embedding our example argument:

{% highlight html %}
<!-- A widget element, and the Argumenta Widgets script. -->
<div class="argument-widget" data-repo="qualiabyte/the-value-of-bitcoin-for-the-99%"></div>
<script src="https://argumenta.io/widgets.js"></script>
{% endhighlight %}

## Argumenta API

The [Argumenta API][Argumenta-API] provides a RESTful interface to
Argumenta data in JSON form. Current resources include Users, Repos,
Arguments, Propositions, Tags, Discussions, Comments, and Search.

Read access is enabled for general use, and cookie-based authenticated
sessions allow account creation, login, and publishing.  It's used by
Argumenta widgets, whether embedded on Argumenta.io or other sites,
and can be used by third-party applications.

## Public and Open Source

Argumenta is built upon an open source web application available for
anyone to run and modify, with both server-side ([Argumenta][Argumenta]) and
client-side ([Argumenta Widgets][Argumenta-Widgets]) components. It's
released under the MIT license.

## Get Involved!

We'd love to have you join the Argumenta community!

As a user, you can get started today by creating an account at
[Argumenta.io][Argumenta.io].

As a developer, you should have a look at our GitHub repos for the
server ([Argumenta][Argumenta]) and widgets
([Argumenta Widgets][Argumenta-Widgets]). The server is written in
CoffeeScript for Node.js, and the widgets are pure JavaScript.

[Argumenta]: https://github.com/argumenta/argumenta
[Argumenta.io]: https://argumenta.io
[Argumenta-Widgets]: https://github.com/argumenta/argumenta-widgets
[Argumenta-API]: https://github.com/argumenta/argumenta/blob/master/doc/README.API.markdown
[Argument-Records]: https://github.com/argumenta/argumenta/blob/master/lib/argumenta/objects/argument.coffee#L72-L102
