# Repository Structure

This repository uses Git submodules to include related project repositories while keeping their development separate.

The main repository is:

```text
MobyPhish
```

The following repositories are included as submodules:

```text
study-sim
pki-chrome
```

#### Development for `study-sim` and `pki-chrome` should happen in their own repositories. The `MobyPhish` repository only tracks which commit of each submodule it currently points to. It is the repository that consolidates all MobyPhish development.
---
# Adding a Submodule

From inside the `MobyPhish` repository, run:

```bash
git submodule add https://github.com/<ORG-NAME>/<repo-name> <repo-name>
```

Then commit the submodule references:
```bash
git add .gitmodules <repo-name>
git commit -m "Add submodule"
git push
```
---

# Cloning This Repository

When cloning `MobyPhish`, use:

```bash
git clone --recurse-submodules https://github.com/MobyPhish/MobyPhish.git
```

If you already cloned the repository without submodules, run:

```bash
git submodule update --init --recursive
```

---

# Updating Submodules

If `study-sim` or `pki-chrome` is updated in its own repository, the `MobyPhish` repository will not automatically point to the latest version.

To update the submodule reference in `MobyPhish`, run:

```bash
cd study-sim
git pull origin main
cd ..

cd pki-chrome
git pull origin main
cd ..
```

Then commit the updated submodule pointers:

```bash
git add study-sim pki-chrome
git commit -m "Update submodule references"
git push
```

If only one submodule changed, only update and commit that one.
