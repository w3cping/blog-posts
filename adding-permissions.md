# Adding another permission? Questions and suggestions

So, you're thinking of adding a new permission prompt to the Web platform? Specification authors and feature designers may find this list of questions useful to think through.

This was inspired by discussions at the [W3C Workshop on Permissions and User Consent](https://www.w3.org/Privacy/permissions-ws-2018/) held last September in San Diego. A [full workshop report](https://www.w3.org/Privacy/permissions-ws-2018/report.html) is available from two days of discussions, covering the challenges of asking for permission, explaining it in context and designing a platform for permissions that are neither intrusive nor fatiguing. That discussion is ongoing (and builds from a [workshop on trust and permissions](https://www.w3.org/2014/07/permissions/) from 2014), but we hope these questions are a starting point for considering new (and existing) permissions right now.

## Designing Web features with permissions

1. Is this feature important for the Web platform?

   Specifically, is this feature important functionality that is consistent with the Web's model of privacy, security, accessibility and permissionless innovation? The Web need not be identical to every other software platform, and the distinctive features of the Web -- that software doesn't need to be vetted to operate, that documents and software co-exist, that users can be free from danger and intrusion when visiting a page, that interoperability is available among a wide range of devices and agents -- are essential to its ongoing success.

2. Does this feature require explicit permission?

   Access to data, sensors and capabilities can be designed in a way that permissions are implicit. For example, drag-and-drop doesn't require interrupting the user to confirm whether they want to share a particular file -- instead, the user's action shows that they already want to provide access to a file onto a specific page/function. Can your feature be designed in this way?

   For example, we could design a "location picker" rather than a geolocation permission. User agents could implement an input type where the user selects either her current location or a named location that she has saved and often wants to search about.

   Adrienne Porter Felt's diagram can help determine whether an explicit permission is required. If this feature can be designed to have accountability and mitigations without prior permissions, that can reduce user fatigue without incurring irreparable harm.

   ![Flowchart on permissions from Adrienne Porter Felt.](images/permission-flowchart.png)

3. What capabilities are implicated by the resource, sensor or functionality that you're adding?

   Asking users to give permission to a piece of data they don't understand is not helpful. (Acronyms definitely fall into this category.) If the resource provides the site with a capability similar to some other resource or sensor, then there are reasons to consider this the same permission.

   Consider also what can be inferred by access to a sensor or piece of personal data that may not be generally obvious. Research has shown: that accelerometer data might reveal the contents of typing; that light sensors might reveal activity on other devices; that photo files often include invisible geolocation metadata.

4. What is the duration and persistence of your permission?

   Different user agents may handle persisting permission in different ways. Considering duration and persistence ahead of time are useful, though. As user's attitudes and conditions will change,limited duration or expiration may be important. If a permission is requested for some future, ongoing or recurring functionality, then additional features are typically necessary for *accountability*, specifically:

   * transparency: notice for ongoing, background or not-just-in-time actions can be challenging, but ambient notice and asynchronous notice are some options. Without that notice, a user who granted permission in the past and forgot (or someone else granted the permission on their device, or a device had multiple users, or the user previously made a decision in a different context) will not have effective means to update their choices.

   * revocability: easy access to withdraw permission is generally useful but especially important in cases of ongoing permission.

5. How will users understand how collected personal data will be used, who has access to it, how long it will be retained and how they can access or delete it?

   In the past, we have sometimes included in specifications the requirement that sites use their own expressive HTML to explain how a capability will be used and their choices regarding it prior to making a browser-mediated permission request. Our experience has shown this option to be very frequently ignored by sites, even when sites may be required by local laws to get such informed and specific consent.

   We believe ongoing research on this problem could help explore whether some purpose specification within browser-mediated permission-granting UI could be managed in a way that doesn't violate trust boundaries. (This debate is at least ten years old, but we're facing many of the same problems and needs today.) For example, [iOS provides a "usage description string"](https://developer.apple.com/design/human-interface-guidelines/ios/app-architecture/requesting-permission/) from the app developer on dialogs for location and photos permissions.

6. What conditions are necessary for this new permission?

   Typically, secure contexts are necessary in order for a user to know who is asking for a permission (otherwise, _who_ would also contain any set of network attackers). Is this functionality only for top-level browsing contexts, or also for embedded third-party frames? Does a permission grant background access or only when a tab is active/visible? Background, invisible access requires different affordances for meaningfully explaining and obtaining user permission.

## How to ask for permission on the Web

While W3C standardization discussions tend to focus on the design of features, web developers and site owners are more directly involved in asking users for permission on the Web sites they develop, author or control. This is surely a non-exhaustive list, but these may be good principles to keep in mind.

* Ask for permission in context and just in time.

* Progressive enhancement: ask for only the permission you need and prepare to gracefully handle cases where a capability is not available.

* Explain the implications of a permission before prompting the user, in a way that is accessible and localized. _Who_ is asking, _what_ are you asking for, _why_ do you need it?

* Users can and will change their minds. Don't assume that a permission granted once guarantees permanent access; nor that a permission refused means a user will never choose to accept some functionality. Set expiration of permissions to a reasonable duration, so that users are reminded and have a chance to renew or change their stated preferences.

---

Are there additional questions you ask when considering a new permission? Or changes to these questions? There's a [repo for the adding permissions guide](https://github.com/w3cping/adding-permissions) where issues and pull requests would be welcome, and there's interest in integrating some or all of these questions into the more exhaustive [security and privacy questionnaire](https://w3ctag.github.io/security-questionnaire/) that the TAG and PING use and maintain.

---

Image credit: the flowchart above is from Section 8.1 of [Adrienne Porter Felt's Ph.D. thesis](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-185.pdf)
