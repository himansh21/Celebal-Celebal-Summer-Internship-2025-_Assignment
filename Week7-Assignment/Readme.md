
# Azure DevOps Assignment: Access Control, Branch Policies, and Pipelines

---

## 1. Create a Project with User Groups and Apply Group Policies

**Steps:**

- Sign in to Azure DevOps at https://dev.azure.com
- Click on **"New Project"**
  - Enter project name (e.g., `DevOpsAccessManagement`)
  - Set visibility to **Private**
  - Click **Create**

**Create User Groups:**

- Navigate to **Project Settings > Permissions**
- Click on **New Group** and create:
  - `Project Administrators`
  - `Contributors`
  - `Viewers`

**Add Users to Groups:**

- Open any group
- Go to **Members → Add**
- Add users via email and click **Save**

**Set Permissions:**

- For Contributors: Allow repo access but restrict policy editing
- For Viewers: Read-only access
- For Admins: Full access to repo, boards, and pipelines

---

## 2. Apply Branch Policies (Only Admin Can Access Master Branch)

**Steps:**

- Go to **Repos → Branches**
- Click the three-dot menu (⋯) next to `master`
- Select **Branch Policies**

**Enable:**

- Minimum number of reviewers (e.g., 1 or 2)
- Check for linked work items
- Require successful build for PR completion

**Set Branch Security:**

- Go to **Branch Security**
- For `Contributors`:
  - Deny `Contribute`
  - Allow `Create Branch`
- For `Admins`:
  - Allow all permissions

---

## 3. Apply Branch Security and Locks

**Steps:**

- Go to **Repos → Branches**
- Use the ⋯ menu to **Lock** the `master` branch

**Configure Branch Security:**

- Deny `Force Push`, `Delete`, and `Contribute` for Contributors
- Allow full permissions for Admins

---

## 4. Apply Branch Filters and Path Filters

**Steps:**

- Go to **Project Settings → Repos → Branches**
- Select the `master` branch and open **Branch Policies**

**Add Build Validation Rule:**

- Set **Branch Filter** to `master`
- Add **Path Filters**:
  - Include: `src/*`
  - Exclude: `docs/*`

This ensures validation runs only for relevant source code changes.

---

## 5. Apply a Pull Request

**Steps:**

- Create a new branch (e.g., `feature/login`)
- Make changes and commit
- Go to **Repos → Pull Requests → New Pull Request**
  - Set source: `feature/login`
  - Set target: `master`
- Assign reviewers and link work items
- Click **Create Pull Request**
- Merge only after all conditions (review, build) are met

---

## 6. Apply Triggers in Build and Release Pipelines

**Build Trigger in YAML:**

```yaml
trigger:
  branches:
    include:
      - master
      - develop

pr:
  branches:
    include:
      - "*"
````

**Release Pipeline:**

* Go to **Pipelines → Releases**
* Click **New Pipeline**
* Select build artifact
* Enable **Continuous deployment trigger**

---

## 7. Apply Gates to the Pipeline

**Steps:**

* Go to **Pipelines → Releases**
* Click on a **stage**
* Open **Pre-deployment Conditions**
* Enable **Gates**

**Common Gates:**

* Delay before deployment
* Invoke REST API (for status checks)
* Azure Monitor (query metrics, logs)

---

## 8. Allow Contributors to Create Pull Requests but Not Merge

**Steps:**

* Go to **Repos → Branches → Branch Security**
* Select `master`

**Set Permissions:**

* `Contributors`:

  * Allow `Create Branch`
  * Allow `Create Pull Request`
  * Deny `Contribute` and `Complete Pull Request`
* `Project Administrators`:

  * Allow all permissions

This enforces review and prevents unauthorized code merges.

---

## 9. Use Work Items in Pipelines

**Steps:**

* Go to **Boards → Work Items**
* Create a new **User Story** or **Bug**
* Assign it to a team member

**While Creating PR:**

* Link the work item by ID or using `#123` in the description
* Enable **"Check for linked work items"** in branch policy

**In Pipelines:**

* Linked work items appear in build and deployment logs
* Enhances traceability and accountability

---

```


