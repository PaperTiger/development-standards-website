{% include _includes/nav.md %}

## Git

#### Sites
- **Preproduction Sites**: When developing a site that has not been released to production and is still in development, it is safe to code directly in `develop`. This ensures that all new code is automatically deployed to the staging site.
- **Production Sites**: When editing production sites, use Gitflow workflow outlined below.

#### Branches
- `develop` - Used for staging releases.
- `master` (sometimes `main`) - Used for production releases.

---

### Gitflow
We use a modified Gitflow Workflow for branching and QA testing. Gitflow makes sure that unfinished features are never merged into the `master` branch.

Example Scenarios:
* **Feature 1**: A developer has been working on `Feature 1` for months, all his code is on his own branch but has been merging into `develop` to QA his work on the staging site and it is not ready to be pushed live.
* **Feature 2**: There is a new feature that needs to be added to the homepage ASAP. In order to add this new feature, the client wants to be able to QA the work on a staging URL before it is released to the production site. We cannot work directly on the `develop` branch because this feature needs to be released before `Feature 1` is finished and since `Feature 1` is not finished, we need to ensure that none of `Feature 1` code is released to production. We also cannot branch off `develop` because this poses the same problem where `Feature 1` code will be present.

#### Using Gitflow
- Branch off `master` for new features: `git checkout master && git checkout -b feature-branch`.
- Merge `feature-branch` into `develop` to QA on staging: `git checkout develop && git merge feature-branch`
- Merge `feature-branch` into `master` when QA is finished and is production ready: `git checkout master && git merge feature-branch`

#### Basic rules of Gitflow
- <span class="bad">**Never Safe**</span> to merge `develop` into `feature-branch`
- <span class="bad">**Never Safe**</span> to merge `develop` into `master`
- <span class="good">**Always Safe**</span> to merge `master` into `feature-branch`
- <span class="good">**Always Safe**</span> to merge `feature-branch` into `develop`
- <span class="good">**Always Safe**</span> to merge `feature-branch` into `master` when `feature-branch` is production-ready

---

### Hotfixes
Sometimes an urgent and/or small request comes through to fix something on production that doesn't need to be QA'd on staging. In these cases, it is OK to work directly in `master` and push your changes directly to production. When the work is done, make sure to merge `master` into `develop` so staging stays in sync with production.