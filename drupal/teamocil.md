# Teamocil

[Teamocil](https://github.com/remi/teamocil) is a simple tool used to automatically
create windows and panes in [tmux](https://github.com/tmux/tmux) with YAML files.
Similar tools are [byobu](https://www.byobu.org) and [mtm](https://github.com/deadpixi/mtm).

Using teamocil you can get ready to use templates to start working on a project with a single click.

Usually located under `~/.teamocil/example.yml` on a Unix machine.

## Install

```
// Install tmux - https://github.com/tmux/tmux
sudo apt-get install tmux

// Install teamocil - https://github.com/remi/teamocil
gem install teamocil
```

## Create a teamocil template

```
// Create a teamocil template
touch ~/.teamocil/example.yml

// Edit the template
teamocil --edit example
```

## Example of a template

```yml
# ~/.teamocil/example.yml
# Comments start with a "#"

windows:
 - name: Name-Of-My-Project # Appears on the terminal title, do not use spaces or special characters
   root: /var/www/html/example.com # Local folder to execute the scripts
   layout: tiled
   panes: # Several panes, each one accomplishes a task
    - git pull
    - cd web/themes/custom/mytheme && gulp watch
    - ddev start && google-chrome "https://example.ddev.site" # Notice: I usually use ddev for development
    - pstorm . &
    - ssh USER@HOST
    - google-chrome "https://www.example.com"
```

## Start a teamocil defined cli

```bash
# Open a teamocil project
tmux new-session -d 'teamocil example' \; attach
```
