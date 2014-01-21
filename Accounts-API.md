The Accounts API exists to provide a central route through which Ghost can connect to 3rd party accounts and services (like twitter, facebook and github). The aim for this is to operate in a similar way to how Google's Android Account Manager system works: http://www.finalconcept.com.au/article/view/android-account-manager-using-other-accounts

There are two primary problems which this system exists to solve:

1. Multiple Ghost apps connected to the same external account having a single point of request/authentication (rather than multiple/overlapping). The concept for this revolves around requesting a single auth token which is shared between Ghost apps. Any app can request a new token on behalf of Ghost.

2. To attempt to simplify the process of connecting 3rd party services to Ghost, which typically need a registered/recognised origin for an API request - in a similar way to what Jetpack does for WordPress. This may need to run through Ghost.org - but it would be great if it didn't have to.