To contribute, please follow the instructions below.

1. Create a new remote branch for the issue.
    * The branch must originate from the parent branch, which is the parent
      issue branch if there is one or ``master`` branch otherwise.
    * The branch name must capture the issue summary.
    * Use lowerCamelCase for the branch name.

2. Commit and push changes required to the issue branch.
    * Follow [Design Guidelines](
      https://github.com/leonid-konovalov/Guidelines/blob/master/Design.md
      ).
    * Follow the guidelines for the languages you use:
        * [Python](
          https://github.com/leonid-konovalov/Guidelines/blob/master/Python.md
          ),
        * [TeX](
          https://github.com/leonid-konovalov/Guidelines/blob/master/Tex.md
          ).
    * Write concise but good commit messages according to these
      [guidelines](https://cbea.ms/git-commit/).
    * Usually a one line message is sufficient for a small commit.
    * Replace automatically generated commit messages with meaningful ones.
    * Do not use issue or branch names in commit messages.
    * Do not commit
        * temporary files (e.g., *.pyc, *.aux),
        * binary files (e.g., *.pkl, *.pdf),
        * image files,
        * other files that are not suitable for version control (e.g., *
          .ipynb).

3. Finalize the work:
    * [ ] Merge the parent branch into the issue branch;
    * [ ] Resolve merge conflicts if any;
    * [ ] Ensure that all the unit tests passed;
    * [ ] Ensure that UML diagrams updated according to the code changes;
    * [ ] Ensure that existing class documentation is relevant
      for each updated class;
    * [ ] Ensure that existing documentation is relevant
      for each updated method or unit test;
    * [ ] Ensure that existing comments are relevant;
      for each updated method or unit test;
    * [ ] Ensure once again that the guidelines are followed;
    * [ ] Run unit tests one more time when all done.

4. Get the work acceptance:
    * [ ] Create a pull request from the issue branch to the parent branch;
    * [ ] Add relevant reviewers;
    * [ ] If changes requested by a reviewer, repeat steps 2-3.

5. When the pull request is approved, merge the issue branch into the parent
   branch:
    * [ ] Create merge commit even if fast-forward is possible;
    * [ ] Provide detailed commit message;
        * [ ] Make commit message summary match the (updated) issue name;
        * [ ] Do not mention any issues or branch names in the merge commit
          message and ensure that it is not done automatically by a version
          control system;
        * [ ] Try to focus on *why* and *what for*, not *what* changed;
    * [ ] Push the parent branch.

6. Delete the local and remote issue branches.

7. Communicate that the issue is done.
