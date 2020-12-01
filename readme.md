# How to update Liferay Portal

## Disclaimer

This is a quick guide to update your instance of Liferay Portal for no-technical users. If you get stuck in any of the points, please contact me with no fear and I'll try to help you

## On macOS

- [Open the Terminal](https://support.apple.com/es-es/guide/terminal/apd5265185d-f365-44cb-8b09-71a064a42125/mac)
- Go to the Portal directory using the `cd` command (e.g.: `cd /Users/eduardoallegrini/projects/liferay-portal/liferay-portal`)
  - If you don’t have the Portal directory see [how-to-install-liferay-portal](https://github.com/julien/notes/blob/master/portal.md#getting-the-source-code)
- [Run](https://askubuntu.com/questions/740173/how-do-i-run-a-command) `git checkout master` to change the local branch to master
  - If you need to update another branch, you don’t need this guide 😉
  - If you are already in master, the command won’t work but that's fine.
- Run `git clean -fdx` to remove the generated files from the last `ant all` execution
- Run `git status` to see the current uncommitted changes
  - If there are changes and you want to remove them run `git stash`
  - If there are changes and you want to keep them [link-to-commit-guide([WIP](https://dictionary.cambridge.org/dictionary/english/work-in-progress))]
- Run `git remote -v` to see the registered remote branches
  - If you don’t have upstream see [the installation-guide](https://github.com/julien/notes/blob/master/portal.md#last-steps)
- Run `git pull upstream master` to download the latest changes from remote (upstream) to your local (master)
  - If (for some reason) you have committed different changes from master, run `git pull upstream master -f` to _force_ the command
  - If it doesn't work, you might need to [add-a-ssh-key-to-github](https://www.inmotionhosting.com/support/website/ssh/how-to-add-ssh-keys-to-your-github-account/)
- Run `ant all` (wait the 15-20 minutes required for the build)
- Go to the `bin` directory using `cd ../bundles/tomcat-9.0.37/bin/`
  - If it doesn’t work, navigate the path manually: start writing `../` and press [[tab]](https://en.wikipedia.org/wiki/Tab_key) twice (instead of [[enter]](https://en.wikipedia.org/wiki/Enter_key))
  - When `bundles` is selected in the Terminal, press [enter] and again [tab] twice
  - Keep doing this process until you reach `../bundles/tomcat-9.0.37/bin/`
- Run `./catalina.sh run`. In a couple of minutes the Portal will start
  - If it doesn’t work, you might need to [start/config your database](https://github.com/julien/notes/blob/master/portal.md#apache-ant-and-mysql-57)
  - If it doesn’t work, you might need to [format your database](https://www.siteground.com/kb/how_can_i_empty_out_an_sql_database/). **Warning: this will delete all the pages, media and _stuff_ in your Portal**
