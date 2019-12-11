# Grand Rounds Coding Conventions and Standards

We generally document coding conventions here, *especially* for languages
that have automated linters -- which almost all languages have now.

We almost always just adopt a good style guide from the culture of the
language itself. E.g., our Python standards are based on PEP008, and our
Ruby ones are based on the venerable Ruby Style Guide published by Github.

We do make our own changes; note that this repo began life as a fork of
Github's RSG repo, because there were a couple changes we made (e.g., our
Javascript folks insisted on no-trailing-comma-in-lists, even in Ruby).

If your language supports a linter, then adopt the linter's standard
if you can, and use the linter. Same for other beautifiers.  We do not
bikeshed on this stuff if we can at all help it.

We keep centralized linter configuration files here in this repo, and then
pull them into, e.g., our CodeClimate configuration files in other repos.
