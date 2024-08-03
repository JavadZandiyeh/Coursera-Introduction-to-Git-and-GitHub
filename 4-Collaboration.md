# 4 Collaboration
## 4.1 Pull Requests
Pull requests allow you to inform fellow contributors about changes that have been made to a branch in Git. When pulling requests, you can discuss and evaluate proposed changes before implementing changes to the primary branch.

You can eventually merge changes back into the main repository (or repo) by creating a pull request. However, it is important to note that before any changes are made to the original code, GitHub creates a fork (or a copy of the project), which allows changes to be committed to the fork copy even if changes cannot be pushed to the other repo. Anyone can suggest changes through the inline comment in pull requests, but the owner only has rights to review and approve changes before merging them. To create a pull request:

-   Make changes to the file.
-   Change the proposal and complete a description of the change.
-   Click the Proposed File Change button to create a commit in the forked repo to send the change to the owner.
-   Enter comments about the change. If more context is needed about the change, use the text box.
-   Click Pull Request.

When creating multiple commits, a number next to the pull request serves as the identifier for accessing the pull requests in the future. This is important because it allows project maintainers to follow up with questions or comments.

For more information on creating pull requests, click the following link: [Creating a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)

### Pull request merges
You can merge pull requests by retaining the commits. Below is a list of pull request merge options that you can use when merging pull requests.

**Merge commits.** All commits from the feature branch are added to the base branch in a merge commit using the -- no–ff option.

**Squash and merge commits.** Multiple commits of a pull request are squashed, or combined into a single commit, using the fast-forward option. It is recommended that when merging two branches, pull requests are squashed and merged to prevent the likelihood of conflicts due to redundancy.

**Merge message for a squash merge.** GitHub generates a default commit message, which you can edit. This message may include the pull request title, pull request description, or information about the commits.

**Rebase and merge commits.** All commits from the topic branch are added onto the base branch individually without a merge commit.

**Indirect merges.** GitHub can merge a pull request automatically if the head branch is directly or indirectly merged into the base branch externally.

![Pull request merges](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/C4nl1oqQSTu0dZT1j4L98Q_8d0d6fd1b8dc43d2b79ee99e6fd7f5f1_2xl_S7thfUImmrOHv7kbUeYXKDckZ7BSdT8i0PFVVSNhAkIZMmWCrgU7NiIU00sjWjUEXdTuRDaEQa6W7f-W0v1NICHE_LJG8C_HIEk6BCwIPnjA_yXRxCyAxJFIt9B-8r5tvsMYnAvQZ3Dlx7rvCARDCLIpeiDZKWXrA8jqmn-BejbtUSrIGVQvQMD8hqB1-E_hAFZQlhTL1KKlcEUgfAVj4Ujg7zTa8e8srA?expiry=1722816000000&hmac=j3NvINpfUTIhf_53LEFnUatEHt3yuekycmMD5rVg1Ww)


### Git Pull Request Workflow:
1. **Fork the Original Remote Repo**
	- Use the GitHub UI to fork the repository you want to contribute to. This creates a copy of the repo under your GitHub account.

2. **Clone the Forked Remote Repo**
	```
	git clone https://github.com/your-username/forked-repo.git
	cd forked-repo
	```

3. **Create a Branch**
	```
	git checkout -b feature-branch
	```
	- It's good practice to name the branch descriptively according to the feature or fix you are working on.

4. **Commit Changes into the Branch**
	```
	git add .
	git commit -m "Description of the changes"
	```

5. **Rebase Interactively to Clean Up Commits**
	```
	git rebase -i main
	```
	-   This command opens an editor where you can squash, reword, or edit commits.
	-   Squashing commits allows you to combine multiple commits into one.
	-   Rewording allows you to change commit messages for clarity.
	-   Editing allows you to change the content of a commit.

6. **Push the Branch to the Forked Repo**
	```
	git push origin feature-branch
	```
	- Use `git push -f` if rebasing into the main branch (see step 5).

7. **Send a Pull Request**
	-   Go to your forked repository on GitHub.
	-   Click on the "Compare & pull request" button.
	-   Add a title and description for your pull request, then click "Create pull request".

**Note:** Any future pushes to the branch will automatically be added to the pull request. For example:
```
git add new_changes
git commit -m "More changes"
git push origin feature-branch
```
This will update the existing pull request with the new commits.

**Note:** If You Want to Create a New Pull Request, make a new branch and repeat the steps.
```
git checkout main
git pull origin main
git checkout -b new-feature-branch
# Make changes, add, commit, and push
```
By creating a new branch, you can create a separate pull request without affecting the previous one.

**Note:** The effect of using `git rebase -i` in this procedure is to make your pull request more professional and easier to review by maintaining a clean and organized commit history.
-   **Cleaner Commit History**: Combining related commits makes the history easier to read and understand.
-   **Improved Clarity**: Rewriting commit messages can make the purpose of each commit clearer to reviewers.
-   **Better Organization**: Interactive rebase allows you to reorder commits logically.

## 4.2 Code Reviews
Consistent coding standards are essential for large-scale projects, ensuring readability and maintainability. Google's style guides stand as prominent examples of how such norms can be established and adhered to across diverse teams. Code reviews are also essential in order to produce quality code. This reading delves into the principles of code review strategies and the significance of style guides, shedding light on their impact on software development practices and outcomes. You'll explore Google's style guides, learn about diverse code review strategies, and gain insights into the significance of pull request reviews.

### Google style guides
Every major open-source project includes a style guide, which is a set of norms for writing code for that project. When all of the code in a huge codebase is written in the same manner, it is considerably simpler to understand.

You can find the project and style guide for Google code [here.](https://github.com/google/styleguide)

### Code review
Code review, also referred to as peer code review, is the deliberate and methodical gathering of other programmers to examine each other's code for errors. Code review can speed up and simplify the software development process, unlike other techniques. Peer reviews also save time and money, especially by catching the kinds of defects that could sneak through testing, production, and into the laptops of end users.

### Common code review strategies
#### Pair programming
This method of building software places engineers side-by-side, working on the same code together. Pair programming is one of the defining characteristics of Extreme Programming (XP). It seems to integrate code review directly into the programming process and is a fantastic technique for senior engineers to mentor junior team members. However, different approaches to code review might offer greater objectivity because writers and even co-authors often become too familiar with their own work. Compared to other approaches, pair programming can require more staff and time resources.

#### The email thread
With the email thread strategy, a file is sent to the appropriate coworkers through email as soon as a particular piece of code is prepared for review, so they can individually review it. Although this method can be more adaptable and flexible than more conventional approaches, an email thread of suggestions and divergent opinions can become confusing very quickly, leaving the original coder to sort through it all.

#### Over the shoulder
One of the oldest, simplest, and most natural ways to participate in peer code review is the over-the-shoulder technique, which is more comfortable for most engineers than XP's pair programming. When your code is complete, ask a coworker to evaluate it while you explain why you created it that way.

#### Tool assisted
Software-based code review tools, some of which are browser-based or seamlessly integrate into a range of common IDE and SCM development frameworks, are the final form of code review. Software tools enable reviews to happen asynchronously and non-locally, issuing notifications to the original coder when new reviews come in. The tools keep the review process moving efficiently with no meetings and no one having to leave their desks to contribute. Some technologies can also produce vital usage statistics that provide the audit trials and review metrics required for process improvement and compliance reporting.

### Pull request reviews
A pull request (PR) is a procedure where new code is examined before it is merged to create a branch or master branch in GitHub. Before a pull request is merged, reviews give contributors the opportunity to comment on the modifications suggested in the request, accept the changes, or ask for additional changes. Administrators of the repository can mandate that each pull request be accepted before it is merged.

Anyone with read access can review and comment on the changes proposed in a pull request once it has been opened. Additionally, you can make precise changes to code lines that the author can implement right from the pull request. If you are interested in learning more about reviewing proposed changes in a pull request, click [here.](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request)

### Five tips for pull request reviews
Some of the considerations you should have with pull request reviews are:

1.  **Be selective with reviewers:** It's important to select a reasonable number of reviewers for a pull request. Adding too many reviewers can lead to inefficient use of resources, as too many people reviewing the same code may not be productive.
    
2.  **Timely reviews:** Ideally, reviews should be completed within two hours of the pull request being submitted. Delays in reviews can lead to context switching and hinder overall productivity.
    
3.  **Constructive feedback:** Feedback should be constructive and explain what needs to be changed and, more importantly, why those changes are suggested. Friendly and non-accusatory language fosters a positive and collaborative atmosphere.
    
4.  **Detailed pull request description:** The pull request should include a detailed description that covers the changes made in the feature branch compared to the development branch, prerequisites, usage instructions, design changes with comparisons to mockups, and any additional notes that reviewers should be aware of. This information ensures that reviewers have a comprehensive understanding of the changes.
    
5.  **Interactive rebasings:** Interactive Rebasings allow developers to modify individual commits without cluttering the commit history with redundant or unrelated changes. Keeping commits clean and relevant contributes to a more organized and maintainable codebase.
    

### Key takeaways:
-   **Importance of consistent coding standards:** Maintaining uniform coding standards ensures readability and ease of maintenance. Google's style guides serve as prime examples of establishing and adhering to such norms across diverse teams.
-   **Role of code reviews:** Code reviews, or peer code reviews, involve organized examination by fellow programmers, speeding up development and catching defects that might bypass testing, saving time and resources.
-   **Diverse code review strategies:** Pair programming, email threads, over-the-shoulder evaluations, and tool-assisted review strategies offer different levels of collaboration and objectivity, catering to different project needs.
-   **Pull request reviews:** Pull request reviews provide an opportunity for collaborative examination of new code before integration. Accessible to those with read access, PR reviews enable inclusive feedback and ensure code quality through timely and constructive comments.

## 4.3 Managing Projects
1.  **Documentation**
    -   Maintain clear and comprehensive documentation for the project. This includes code comments, README files, and contribution guidelines.

2.  **Refactoring**
    -   Regularly refactor parts of the codebase that are not currently being worked on to improve code quality and maintainability.

3.  **Respond Quickly to Pull Requests**
    -   Reply promptly to pull requests, thoroughly reviewing and understanding any changes proposed.

4.  **Use Issue and Bug Trackers**
    -   Utilize issue and bug trackers to assign tasks and track progress. This helps clarify who is responsible for what.

5.  **Communication Tools**
    -   Implement communication tools like Slack to facilitate efficient team communication and collaboration.

6.  **CI / CD: Continuous Integration and Continuous Delivery**
    -   **CI**: Automate testing to ensure code changes integrate smoothly into the project.
    -   **CD**: Implement incremental rollouts for smooth and reliable deployment of new features.

	**Note:** Continuous Integration (CI) is for automating tests to verify the code’s integrity. Continuous Delivery (CD) is for deploying code changes incrementally to minimize disruption and risk.

### 4.3.1 Pipelines and Artifacts

#### Pipelines

A **pipeline** in the context of CI/CD is a set of automated processes that software developers use to build, test, and deploy their code. The pipeline defines the steps that need to be performed in a specific order to ensure that the code is integrated, tested, and delivered effectively.

##### Common Stages of a CI/CD Pipeline

1.  **Source**:
    
    -   Triggered by changes in the source code repository (e.g., a new commit or pull request).
2.  **Build**:
    
    -   Compiles the source code into executable artifacts.
    -   Ensures that the code compiles correctly and that dependencies are resolved.
3.  **Test**:
    
    -   Runs automated tests (unit tests, integration tests, etc.) to verify code correctness.
    -   Ensures that new changes do not break existing functionality.
4.  **Package**:
    
    -   Packages the built code into distributable formats, such as executable files, Docker images, or libraries.
5.  **Deploy**:
    
    -   Deploys the built and tested code to staging or production environments.
    -   Can include different environments like development, testing, staging, and production.
6.  **Release**:
    
    -   Manages the release of the deployed code, often involving approval processes and rollback mechanisms.
7.  **Monitor**:
    
    -   Monitors the deployed application for performance, errors, and other operational metrics.
    -   Provides feedback to developers for continuous improvement.

#### Artifacts

**Artifacts** are the byproducts of the build process in a CI/CD pipeline. They are the output files that are generated after the source code has been built and packaged. Artifacts can include:

-   Compiled binaries or executables
-   JAR, WAR, or EAR files for Java applications
-   Docker images
-   ZIP or TAR files containing application code
-   Library files (e.g., DLLs, .so files)
-   Documentation files (e.g., generated API docs)
-   Static files for web applications (e.g., HTML, CSS, JS files)

##### Role of Artifacts in CI/CD Pipelines

1.  **Storage**:
    
    -   Artifacts are stored in artifact repositories (e.g., JFrog Artifactory, Nexus Repository) for versioning and retrieval.
2.  **Deployment**:
    
    -   Artifacts are deployed to various environments as part of the deployment stage of the pipeline.
3.  **Testing**:
    
    -   Artifacts are used in testing stages to ensure that the build is correct and behaves as expected.
4.  **Release**:
    
    -   Artifacts are distributed to end-users or customers as part of the release process.

##### Example Workflow with Pipelines and Artifacts

1.  **Code Change**:
    
    -   A developer pushes code changes to the repository.
2.  **Pipeline Trigger**:
    
    -   The CI/CD pipeline is triggered by the code change.
3.  **Build Stage**:
    
    -   The pipeline compiles the code and generates build artifacts (e.g., binaries, Docker images).
4.  **Test Stage**:
    
    -   The pipeline runs automated tests on the build artifacts to ensure correctness.
5.  **Package Stage**:
    
    -   The build artifacts are packaged for deployment.
6.  **Deploy Stage**:
    
    -   The packaged artifacts are deployed to a staging environment for further testing.
    -   If approved, the artifacts are then deployed to production.
7.  **Release Stage**:
    
    -   The artifacts are released to end-users or customers.
8.  **Monitor Stage**:
    
    -   The deployed application is monitored for performance and errors.

By using pipelines and managing artifacts effectively, development teams can ensure that their code is built, tested, and deployed in a consistent, automated, and reliable manner.

## 4.4 Glossary Terms
**CI/CD:** The name for the entire continuous integration and continuous deployment system

**Code reviews:** The deliberate and methodical gathering of other programmers to examine each other's code for errors to increase the code quality and reduces the amount of bugs

**Continuous deployment (CD):** New code is deployed often after it has been automatically built and tested

**Continuous integration (CI):** A system that will automatically build and test our code every time there's a change

**Fix up:** The decision to discard commit messages for that commit

**Forking:** A way of creating a copy of the given repository so that it belongs to our user

**Indirect merges:** GitHub can merge a pull request automatically if the head branch is directly or indirectly merged into the base branch externally

**Issue tracker (bug tracker):** A tracker that shows tasks that need to be done, the state they're in and who's working on them

**Merge commits:** All commits from the feature branch are added to the base branch

**Pipelines:** The specific steps that need to run to obtain the desired result

**Pull request:** A procedure where new code is examined before it is merged to create a branch or master branch

**Squash commits:** The decision add commit messages together and an editor opens to make any necessary changes
