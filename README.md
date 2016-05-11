# Git Process #

[Goal](#goal)

[Concept](#concept)

[Workflow - Basic](#workflow---basic)

[Workflow - Advance](#workflow---advance)

[Conventions](#conventions)

[References](#references)

## Goal ##

This document provide basic knowledge, best practices and conventions using Git in project development.

## Concept ##

### 1. Issue ###

Issue is anything what is problem in project, it can be bug, feature task, idea, question, …. Every issue has a its own number. When you commit code to repository, you MUST add the issue number reference to the commit. It help tracking your change assigned with particular purpose.

### 2. Branch ###

A branch is a parallel version of the main line of development in the repository, or the default branch (usually `master`). Use branches to:

  - Develop features
  - Fix bugs
  - Safely experiment with new ideas
  - Upgrade a library or plugin
  - Remove, revert something
  - Do something else

Branching is a core concept in Git, and the entire Git Branching Model is based upon it. There's only one rule: anything in the `master` branch is always deployable. Because of this, it's extremely important that your new branch is created off of `master` when working on a feature or a fix. Your branch name should be descriptive (e.g., `refactor-authentication`, `user-content-cache-key`, `make-retina-avatars`), so that others can see what is being worked on.

Although branch may be deleted after merge pull request but we should follow convention for reasons:

  - For `consistency` in the whole project, which make convenience and provide useful info to reviewer or reader about what that branch do in general when browse branches or view log.
  - For `organized`, which make having look view folders when search and switch branches in `refs` tree.

### 3. Commit ###

Commit is the way that record change to the repository. Commit messages are important, especially since Git tracks your changes and then displays them as commits once they're pushed to the server. By writing clear commit messages, you can make it easier for other people to follow along and provide feedback.Clear and consistency message help us

  - Generating CHANGELOG.md
  - Recognizing unimportant commits
  - Provide more information when browsing the history

### 4. Pull Request ###

Pull Requests are useful for contributing to projects and for managing changes to shared repositories. Pull Requests provide a way to notify project maintainers about the changes you'd like them to consider. They help start code review and conversation about proposed changes before they're merged into the `master` branch.

### 5. Merging ###

Merging is a process join a branch into other branch, the result is a single collection of files that contains both sets of changes. This usually is performed through by a Pull Request. After this process end, the branch, pull request and relevant issues are closed.

### 6. Tag ###

During development, you can `tag` your `master` to mark specific points in history as being important. Typically people use this functionality to mark release points.

Git uses two main types of tags: lightweight and annotated. Lightweight is just a pointer to a specific commit while are annotated tag stored as full objects in the Git database. Annotated tag are used to mark a stable release.

Using tag convention to ensure that your releases are easily recognized.

## Workflow - Basic ##

![_Image 1 - Overview basic flow_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/nldhauc8ag8mcggyjmyk)

Overview general flow:

- Create a branch
- Add commits
- Open a pull request
- Discuss and review code
- Merge and deloy


### 1. Create a branch ###

![_Image 2 - Create a branch_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/tcjbsigti4g4o1emusar)

When you're working on a project, you're going to have a bunch of different features or ideas in progress at any given time – some of which are ready to go, and others which are not. Branching exists to help you manage this workflow.

When you create a branch in your project, you're creating an environment where you can try out new ideas. Changes you make on a branch don't affect the "master" branch, so you're free to experiment and commit changes, safe in the knowledge that your branch won't be merged until it's ready to be reviewed by someone you're collaborating with.

### 2. Add commits ###

![_Image 3 - Add commits_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/dtg99vqd1rsw8wp1yzwf)

Once your branch has been created, it's time to start making changes. Whenever you add, edit, or delete a file, you're making a commit, and adding them to your branch. This process of adding commits keeps track of your progress as you work on a feature branch.

Commits also create a transparent history of your work that others can follow to understand what you've done and why. Each commit has an associated commit message, which is a description explaining why a particular change was made. Furthermore, each commit is considered a separate unit of change. This lets you roll back changes if a bug is found, or if you decide to head in a different direction.

Each commit MUST reference to an issue, see more in convention section.


### 3. Open a Pull Request ###

![_Image 4 - Open a Pull Request_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/xeegbfgp3o3ein2xjuox)

Pull Requests initiate discussion about your commits. Because they're tightly integrated with the underlying Git repository, anyone can see exactly what changes would be merged if they accept your request.

You can open a Pull Request at any point during the development process: when you have little or no code but want to share some screenshots or general ideas, when you're stuck and need help or advice, or when you're ready for someone to review your work. By using Bitbucket or GitHub's @mention system in your Pull Request message, you can ask for feedback from specific people or teams, whether they're down the hall or ten time zones away.

Each Pull Request MUST reference to an issue, see more in convention section.


### 4. Discuss and review code ###

![_Image 5 - Discuss and review code_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/p2r13trnbtbcqjqdvodt)

Once a Pull Request has been opened, the person or team reviewing your changes may have questions or comments. Perhaps the coding style doesn't match project guidelines, the change is missing unit tests, or maybe everything looks great and props are in order. Pull Requests are designed to encourage and capture this type of conversation.

You can also continue to push to your branch in light of discussion and feedback about your commits. If someone comments that you forgot to do something or if there is a bug in the code, you can fix it in your branch and push up the change. GitHub will show your new commits and any additional feedback you may receive in the unified Pull Request view.

### 5. Deploy ###

![_Image 6 - Deploy_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/ttw240urk7uwu6efyd1a)

Once your pull request has been reviewed and the branch passes your tests, you can deploy your changes to verify them in staging or production depend on your development model. If your branch causes issues, you can roll it back by deploying the existing stable version.

### 6. Merge ###

![_Image 7 - Merge_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/ibekbnfjvapm4hxarmrl)

Now that your changes have been verified, it is time to merge your code into the `master` branch.

Once merged, Pull Requests preserve a record of the historical changes to your code. Because they're searchable, they let anyone go back in time to understand why and how a decision was made.

During development, you can `tag` your `master` to mark it as a stable release.

## Workflow - Advance ##

In company, use this flow as main flow.

### 1. The main branches ###

  - `master`: a production-ready branch what we could use a Git hook script to automatically build and roll-out the project to our production servers everytime there was a commit on `master`.
  - `develop`: consider to be the main branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release.

When the source code in the `develop` branch reaches a stable point and is ready to be released, all of the changes should be merged back into `master` somehow(by release branches) and then tagged with a release number.

Depend on project, staging can be either `develop` branch or release branches.

### 2. Supporting branches ###

  - Feature branches:

    - May branch off from:  `develop`
    - Must merge back into:  `develop`
    - Branch naming convention: see convention section

  - Release branches: hold candidate releases, with only bug fixes and no new features

    - May branch off from:  `develop`
    - Must merge back into:  `develop` and `master`
    - Branch naming convention: see convention section

  - Hotfix branches:

    - May branch off from: `master`
    - Must merge back into:  `develop` and `master`
    - Branch naming convention: see convention section

### 3. Flow ###

![_Image 8 - Overview advance workflow_](http://res.cloudinary.com/pm-greenglobal/image/upload/w_600/vttlpc1q0wen30yqvttc)

## Conventions ##

### 1. Issue reference ###

When you commit code to repository, you MUST add issue reference for every commit. It help tracking your change assigned with particular purpose. We can reach to this using keywords supported in GitHub, Bitbucket, using hashtag and issue's number.

For example:

  - In GitHub, include `#12` into commit to mark the commit with the 12 issue.
  - In Bitbucket, it is `see #12`. Some other keywords you can find more in their document.

Notice:

  - Alway reference issue in commit message and PR's description.

### 2. Branch naming ###

Format:

  < **type** > **/** < **scope** > **/short-useful-descriptive-subject**

  - _type_: the different types of branches we may use are:

    - _feat_: add functions, features
    - _hotfix_: hotfix
    - _fix_: fix bug
    - _docs_: documentations
    - _style_: formatting styles
    - _refactor_:
    - _test_: add missing tests
    - _chore_: maintain, remove unnecessary files
    - _release_: only for release branches

  - _scope_: anything identify where the issue belong to, should shorten in 1 word
  - _subject_: a description should short, useful, descriptive describe, separate words by hyphen (-) or underscore (_)

Examples:

  - feat/User/login-facebook
  - bug/Comment/delete-fail
  - chore/remove-unused-file
  - style/User/format-code
  - doc/User/edit-class-document
  - test/User/add-test-registration

Notice:

  - Keep your mindset that `master` branch is product branch, it's should alway free bug.
  - Don't name your branch like `master`, `develop`. These branch is for special purpose environment: `master` is production and `develop` is development.

### 3. Commit message ###

Format:

  < **type** >(< **scope** >): < **subject** >

  <BLANK LINE>

  < **body** >

  <BLANK LINE>

  < **footer** >

  - _type_: The same _type_ in branch name

  - _scope_: The same _scope_ in branch name

  - _subject_:  The similar _subject_ in branch name Title of issue should short, useful, descriptive describe

    - use imperative, present tense: "change" not "changed" nor "changes"
    - don't capitalize first letter
    - no dot (.) at the end

  - _body_: body of commit say in detail what this commit change

  - _footer_: other information, ex: reference issue

Example:

```
feat(User): login Facebook

Login Facebook

see #12
```

```
fix(User): fix bug login Facebook

Bug Facebook login, site show an addition information when connect fail

see #13
```

Notice:

  - Always reference issue in commit message.
  - Don't tag command closing issue in Bitbucket commit message. Because closing issue mechanism in Github and Bucket is difference. If the commit is in a non-default branch on Github, the issue will remain open and it'll only auto closed after PR merged. But Bitbucket close it when push code. Let this closing for reviewer, he will close it when merge PR.

### 4. Create pull request ###

If we are following above conventions, we easily deal with creating a PR. For example Bitbucket will take a first line in commit message to fill to PR's title and the remaining part to PR's description.

Github support only auto closing issue after PR merged through using `close #12` in commit message but not Bitbucket. Therefore you should add this closing line to PR's description in order to close what issue you done in Bitbucket.

By incorporating certain keywords into the text of your Pull Request, you can associate issues with code. When your Pull Request is merged, the related issues are also closed. For example, entering the `closes #32` would close issue number 32 in the repository.

Notice:

  - Always reference issue in PR's description.
  - Include issue closing in end of PR's description if you want to close the issue.

### 5. Tag Version ###

When marking release point, we must use tag named according to Semantic Versioning. Prefix `v` and following an Semantic Versioning.

Given a version number MAJOR.MINOR.PATCH, increment the:

  - MAJOR version when you make incompatible API changes,
  - MINOR version when you add functionality in a backwards-compatible manner, and
  - PATCH version when you make backwards-compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

We can use pre-release label to indicates that the version is unstable: alpha, beta, rc and patchs version for them.

Precedence is determined by the first difference when comparing each of these identifiers from left to right as follows:

  - Major, minor, and patch versions are always compared numerically. Example: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1
  - When major, minor, and patch are equal, a pre-release version has lower precedence than a normal version. Example: 1.0.0-alpha < 1.0.0
  - Numeric identifiers always have lower precedence than non-numeric identifiers. A larger set of pre-release fields has a higher precedence than a smaller set, if all of the preceding identifiers are equal. Example: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0

## References ##

1. [https://guides.github.com/introduction/flow](https://guides.github.com/introduction/flow)
2. [http://nvie.com/posts/a-successful-git-branching-model/](http://nvie.com/posts/a-successful-git-branching-model/)
3. [http://stackoverflow.com/questions/273695/git-branch-naming-best-practices](http://stackoverflow.com/questions/273695/git-branch-naming-best-practices)
4. [https://gist.github.com/stephenparish/9941e89d80e2bc58a153](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)
5. [https://confluence.atlassian.com/bitbucket/resolve-issues-automatically-when-users-push-code-221451126.html#Resolveissuesautomaticallywhenuserspushcode-IncludingIssuesinaCommitMessage](https://confluence.atlassian.com/bitbucket/resolve-issues-automatically-when-users-push-code-221451126.html#Resolveissuesautomaticallywhenuserspushcode-IncludingIssuesinaCommitMessage)
6. [https://help.github.com/articles/closing-issues-via-commit-messages/](https://help.github.com/articles/closing-issues-via-commit-messages/)
7. [https://git-scm.com/book/en/v2/Git-Basics-Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
8. [http://semver.org/](http://semver.org/)
