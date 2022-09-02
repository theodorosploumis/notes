# Teamocil

[Teamocil](https://github.com/remi/teamocil) is a simple tool used to automatically
create windows and panes in [tmux](https://github.com/tmux/tmux) with YAML files.
Similar tools are [byobu](https://www.byobu.org) and [mtm](https://github.com/deadpixi/mtm).

Using teamocil you can get ready to use templates to start working on a project with a single click.

Usually located under `~/.teamocil/example.yml` on a Unix machine.

## Example

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
    - lando start && google-chrome "https://example.ddev.site" # I usually use ddev for development
    - pstorm . &
    - ssh USER@HOST
    - google-chrome "https://www.example.com"
```

## cli command

```bash
# Open a teamocil project
tmux new-session -d 'teamocil example' \; attach

# Edit a teamocil template
teamocil --edit example
```
