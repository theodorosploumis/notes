# Debugging software

## General notes

- Finding a bug is different that fixing it
- We spend more time debugging than programming
- Debugging is part of the process
- Do a research before starting (eg on Search Engines, ask a colleague etc)
- Understand the system/app before starting
- Get a fresh view, eg ask another person to check the problem
- Try to reproduce the problem on a clean installation
- Use log files (eg syslog) and an audit trail
- Format logs (eg with multitail)
- Show contextual info on the Logs (eg browser, env, user, date etc)
- Always take notes and keep logs
- Create small experiments with git branches
- Create a script/method that can recreate the app for every test (eg with docker, clean backup etc)
- Prefer to store log files on the system and not in the (web) screen
- Start with the "easy" to fix errors
- Do not debug online. Make a local copy of the app. This may not be the case where the problem is from the server setup
- Thinking stragetically is more important than applying funcy debug tools
- "Hard to fix" bugs are the one that appear when two "bug free" components interact to create the bug
- Prepare to continue the debug on another day
- If your solution is important publish (eg as a patch) it on the appropriate place (eg on Drupal.org issue)
- Document the process when the bug is fixed
- Sometimes you have to live with a bug wihout fixing it

## Debugging iteration

- Change one thing at a time
- Test the change
- Repeat
- "Cheap" tests should come first
- Common problems testing should come first
- Try to eliminate the error sources from each test
- git is your friend. Use `git diff`, `git blame`, `git anotate`

## Debug in Drupal

- Disable modules in sequence
- Disable theme
- Clear cookies
- Use modules `devel` and co

## Resources

- <http://debuggingrules.com>
- [Drupal modules for debugging](https://www.drupal.org/project/project_module?f%5B0%5D=&f%5B1%5D=&f%5B2%5D=im_vid_3%3A59&f%5B3%5D=sm_core_compatibility%3A9&f%5B4%5D=sm_field_project_type%3Afull&f%5B5%5D=&f%5B6%5D=&text=debug&solrsort=score+desc&op=Search)
- [Drupal: Debugging Twig templates](https://www.drupal.org/node/1906392)
- [Drupal: Setting up remote debugging](https://www.drupal.org/node/2694471)
- [Profiling Drupal](https://www.drupal.org/node/2818707)
