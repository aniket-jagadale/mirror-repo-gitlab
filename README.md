# 🚀 Mirroring a Repository from GitLab to GitHub

This repository, **`mirror-repo-gitlab`**, demonstrates a one-way **push mirror** from **GitLab** (the primary source) to **GitHub** (the destination mirror). This ensures that all commits and merges performed on GitLab are automatically synchronized to GitHub.

---

## 🛠️ Setup Steps and Commands

### Step 1: Initialize Repositories

1.  **Create GitLab Project:** A new project named `mirror-repo-gitlab` was created on GitLab. 
![for the initial commit on GitLab](/img/Screenshot%20(238).png)
2.  **Create GitHub Repository:** A corresponding repository, also named `mirror-repo-gitlab`, was created on GitHub. 
![for the initial commit on GitHub](/img/Screenshot%20(237).png)

### Step 2: Configure Repository Mirroring

1.  **Set up Push Mirror in GitLab:** In the GitLab project settings (**Settings** $\rightarrow$ **Repository** $\rightarrow$ **Mirroring repositories**), the **GitHub repository's HTTPS URL** and a **Personal Access Token** were used to configure a **Push** mirror.

    * **Repository URL:** `https://******@github.com/aniket-jagadale/mirror-repo-gitlab.git`
    * **Direction:** Push
    * This ensures changes pushed to GitLab are automatically pushed to GitHub.
    ![confirming the mirroring setup](/img/Screenshot%20(239).png)

### Step 3: Initial Clone and File Creation (index.html)

The repository was cloned from the GitLab URL, and the first file (`index.html`) was created, committed, and pushed.

| Action | Command | Explanation |
| :--- | :--- | :--- |
| **Clone** | `git clone [GitLab HTTPS URL]` | Clones the empty GitLab project locally. |
| **Create File** | `vim index.html` | Creates the `index.html` file locally. |
| **Add** | `git add index.html` | Stages the file for commit. |
| **Commit** | `git commit -m "adding index.html page"` | Commits the changes locally. |
| **Push** | `git push origin main` | Pushes the commit to the GitLab `main` branch. |

**Result:** After this push to GitLab, the mirroring process automatically pushed the commit to GitHub.
![ on GitLab ](/img/Screenshot%20(241).png)
![GitHub showing `index.html` added](/img/Screenshot%20(242).png)

### Step 4: Branch and Second File Creation (about.html)

A new branch was created, and the second file (`about.html`) was added and pushed to this new branch on GitLab.

| Action | Command | Explanation |
| :--- | :--- | :--- |
| **Create Branch** | `git checkout -b about` | Creates and switches to a new branch named `about`. |
| **Create File** | `touch about.html` | Creates the `about.html` file in the new branch. |
| **Add** | `git add about.html` | Stages the file. |
| **Commit** | `git commit -m "adding about.html page"` | Commits the changes locally. |
| **Push** | `git push origin about` | Pushes the new `about` branch and its commit to GitLab. |

### Step 5: Merging Changes and Automatic Synchronization

1.  **Create Merge Request (GitLab):** A **Merge Request** was created on GitLab to merge the `about` branch into the `main` branch.
2.  **Merge the Request:** The Merge Request was submitted and merged on GitLab.
![showing the successful merge on GitLab](/img/Screenshot%20(240).png)

**Final Result:** Once the merge was completed on GitLab's `main` branch, the mirroring service automatically updated the `main` branch on the **GitHub** repository, resulting in `about.html` being present on both platforms' primary branches.