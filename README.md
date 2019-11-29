# GitLab - Show members in a hierarchy of groups and subgroups

This is a fork of https://github.com/alejandropg/gitlab-members. It was altered to show **all** groups of a specifiable GitLab server with all the members in a hierarchy of groups, sub-groups, and projects with the access level.

Right now GitLab doesn't allow you to search a member in this kind of hierarchies, so I hope this simple code helps you to find and administer your users.

## How to use

```bash
./build.sh ; # Will create a Python virtual env and install this module dependencies
. venv/bin/activate ; # Activate the Python virtual env
python -m gitlab <personal-access-token> <gitlab-server-url>
```

As you can see you have to pass your `<personal-access-token>` to access to the GitLab API. You can create a specific one in <https://your-gitlab.domain.com/profile/personal_access_tokens>.

The second argument is the complete server url of your GitLab instance.

For example in a hierarchy like:

```
organization
  John
  Laura
  sub-group
    Sara
    Marco
    project-1
      Pietro
      Berta
organization-2
  John
```

You will get an output like:

```bash
$ python -m gitlab smkcoa34rH_pl23QFKxL https://your-gitlab.domain.com/
root group - organization
    member - 837493 - john - 50
    member - 208483 - laura - 30
    subgroup - 8479355 - organization/sub-group
        member - 348473 - sara - 30
        member - 483909 - marco - 30
        project - 7893921 - project-1 - private
            member - 1230878 - pietro - 40
            member - 499037 - berta - 40
root group - organization-2
    member - 837493 - john - 50
```
