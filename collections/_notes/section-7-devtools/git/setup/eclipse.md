---
layout: post
title: Setup Using eclipse
permalink: /:collection/git/setup/eclipse
---

1. Right click on your eclipse project -> Team -> Share project
2. Choose git from the list shown; check the box asking create or use repository -> click on create repository and click finish. - This will create a local git repo. (Assuming you already have git installed )
3. Right click on project -> Team -> Commit - Select only the files you want to commit and click on Commit. - Now the files are committed to your local repo.
4. Go to git repositories view in eclipse ( or Team -> Show in repositories View)
5. Expand the git repo of your project and Right click on Remotes -> Create Remote
6. Remote name will appear as origin, select 'Configure Push' Option and click ok
7. In the next dialog, click on change next to URI textbox and give your git url, username, password and click on 'Save and Push'. This configures git Push.
8. For configuring Fetch, go to Git Repositories -> Remote -> Configure Fetch -> Add -> Master Branch -> Next -> Finish -> Save and Fetch
9. For configuring Master Branch, Branch -> Local -> Master Branch -> Right click and configure branch -> Remote: origin and Upstream Branch : refs/heads/master -> click ok
