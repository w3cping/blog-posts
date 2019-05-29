Privacy Anti-Patterns in Standards
===

What is the W3C Privacy Interest Group (aka PING)
---
The Web suffers from large scale, frequent, and often invisible privacy
violations.  These pervasive privacy problems threaten the Web's position
as a dominate application platform and information distribution system.

<abbr title="Privacy Interest Group">PING</abbr> is an
[Interest Group](https://www.w3.org/2019/Process-20190301/#GroupsWG) with
the mission of improving privacy in Web standards, so that Web users can be
confident that they can use the Web without putting their privacy at risk.

PING tries to improve web privacy in several ways, including:

* reviewing newly proposed standards to remove, modify or restrict privacy
  threating features.
* revising existing standards to improve the privacy-properties of existing
  functionality.
* developing and sharing guidelines for standards authors, so that future
  additions to the Web platform can be designed to be private-by-default.

This post discusses three reoccurring "anti-patterns" PING sees in Web
standards, or reoccurring issues in proposed standards that are harmful to Web
privacy.  This is not intended to be a complete list, nor is it intended to
call out or "shame" any particular existing standards; instead, the goal is to
demonstrate frequently recurring problems we see in standards, to explain why
they are harmful to the goal of a privacy-respecting Web, and to provide
guidelines for how future standards can be designed to respect privacy.


Three Privacy "Anti-Patterns" in Web Standards
---
In this section we detail three reoccurring problems that harm privacy in
Web standards. Though each of these occur in many (many!) standards,
we're intentionally *not* calling out or mentioning any specific standards,
to keep the descriptions as general and pattern based as possible.  If anyone
would like more information or examples of any of the below though, feel
free to contact the author or anyone on PING for more specifics.


### Strictly Defined Functionality, Loosely-Defined Protections
Many standards strictly describe functionality that browser vendors should
implement, but are very loose or vague about the mitigations browsers should
deploy to protect users from possible privacy harms. In the extreme cases,
standards will have many pages of text describing, in precise language,
how new functionality will work, followed by a paragraph or two saying
"implementers can vary from the standard at any time to protect users privacy."

While well meaning, patterns like the above (strictly defined functionality,
loosely-defined protections) are harmful to Web privacy for several reasons.

First, though it might seem that weakly / broadly defined mitigations maximizes
implementer flexibility in protecting user privacy, the opposite ends up
being true; weakly defined mitigations make it extremely difficult to protect
user privacy; websites end up assuming the defined functionality, and
privacy-oriented implementers end up with unmanageable compatibility
problems if they alter the behavior of these privacy-harming, but expected
features.

Second, this pattern boils down to a "punt" on dealing with the privacy
risks of the new functionality. In some cases this is because future standards
are expected to address the current harm (bad!), in other cases because
there is no commonly agreed to solution for dealing with the harm (bad!), and
in yet other cases its because the standards authors believe the benefits of
the new functionality of weigh the privacy harms.  In all cases, the end
result is the addition of new privacy risk to a platform already struggling
with tremendous privacy problems, something we believe is harmful
for the Web platform.

**Solution:** Standards should define privacy protections just carefully
and precisely as they define new functionality.  Once functionality hits
the Web, its *extremely* difficult to change its behavior or roll it back.
Protections need to be specific, as mandatory as the defined behavior, and
defined from day one to protect Web privacy.


### Uncommon Use Cases, Global Availability
A second privacy-harming pattern we see in Web standards is the
over-availability of new functionality; powerful new functionality aimed at
niche use-cases, being made globally available (e.g. third-party code,
third-party frames, without permission prompt, user gesture, or user
notification, etc). Many of these powerful new browser capabilities end up
beneficial to users on only a small number of websites, but leveraged
for [passive](https://panopticlick.eff.org)
[fingerprinting](https://browserleaks.com) on a large number of websites.

This pattern of leveraging powerful-but-rarely-used functionality for
user identification (instead of its intended, user-serving purposes) can
be observed in [popular user-tracking (e.g. privacy violating)
tools](https://github.com/Valve/fingerprintjs2) and the changes
[privacy-focused](https://2019.www.torproject.org/projects/torbrowser/design/)
[implementers](https://github.com/brave/brave-browser/wiki/Deviations-from-Chromium-(features-we-disable-or-remove)
need to make to keep their users private.

We emphasize that we don't think that this new functionality isn't useful;
it is! We only mean to highlight that its also dangerous to privacy, and should
be treated as such.

**Solution:** Websites should not be able to access rarely needed
functionality, functionality aimed at very specific, uncommon use cases.
Instead, websites should be only be allowed to use powerful new features
when accessed from privileged positions (e.g. first-party code running
in a first party context, but not third-party frames, etc.) or when users
have given some signal they desire the additional functionality (e.g.
a permission prompt, a user gesture, etc.).  While the specific "gating"
mechanisms will vary from case to case (and thus is beyond the scope of this
blog post), almost any "gating" is better than global access. Increasing the
power of the Web, while improving user privacy, requires keeping rarely needed
functionality rarely available.

### "No Worse Than The Status Quo"
A third privacy harming anti-pattern in Web standards concerns the bar
standards authors hold them to when introducing new privacy-risking
functionality. Frequently standards authors start from the position that
new standards should not make Web privacy worse. The result is that new
standards often make existing sensitive information available in additional
locations. This is extremely harmful for Web privacy.

Even just replicating sensitive, or user identifying, information
in new locations makes future mitigation more difficult.  Instead of needing
to fix or remove one privacy harming feature from the Web (already extremely
difficult), browser vendors need to untangle twice as many expected features
from the Web. Just replicating existing fingerprinting surface amounts to
further technical debt that we in the privacy community need to pay down.

**Solution:** New standards should treat all additional privacy risk as equally
problematic. The appropriate measure for new standards isn't "marginal
increase in privacy risk"; its "could the functionality in the standard
be used to harm user privacy." Put differently when you find you're digging
yourself into a hole, the first thing to do is to stop digging. The Web is
already rife with difficult privacy problems, new standards should entrench
the problem further.


The Importance of Privacy in Standards
---
In conclusion, our goal in this post is to highlight the critical role
standards play in protecting Web privacy, and thus confidence in the Web
as an information an application platform in general. Web standards can
either play an invaluable role in building a "private by default" platform
we can be proud of, or it can take the form of a mass of privacy-risking
functionality that implementers need to mutate, violate and deviate from
to keep users private and protected.

The three anti-patterns described above are a significant part of how
the Web wound up in its problematic, frequently privacy-harming state. Fixing
these anti-patterns is a necessary part of building a humane, privacy
respecting Web.
