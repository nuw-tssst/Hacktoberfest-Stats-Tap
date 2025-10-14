# GitHub Hacktoberfest Stats "Tap"

> Not for code contributions - the source code is remote.

Orchestrates API-fetching to a private core repo for Hacktoberfest GitHub PR statistics:
* CI searches regularly between YYYY-09-30-10:00:00 and YYYY-11-01-14:00:00 UTC for 
  * valid PRs merged to repos
  * accepted valid PRs not merged to repos
* Valid PRs are
  * to repositories with the 'hacktoberfest' topic or have the 'hacktoberfest-accepted' label, and 
  * created between YYYY-09-30-10:00:00 and YYYY-11-01-14:00:00 UTC, and
  * not be labelled either 'spam' or 'invalid' if not labelled 'hacktoberfest-accepted', and
  * not a draft PR
* Accepted PRs must be valid and, between YYYY-09-30-10:00:00 and YYYY-11-01-14:00:00 UTC, either
  * merged, or
  * open and labelled with 'hacktoberfest-accepted'
* Excludes PR review acceptance criteria on assumption of being merged if all code owners approve
* If YYYY-11-01-14:00:00 UTC has not yet occurred, falls back to the most recent day in October
* Does not account for PR disqualification aside for PR labels 'spam' and 'invalid'
* Assumes included repositories meet other requirements to be valid for hacktoberfest
  * includes fork repos, owned by PR creators or not, assuming they meet acceptance criteria
  * accepted PR data for repos removed following API-fetching day(s) will be included in the stats 
