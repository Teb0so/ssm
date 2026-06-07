# Super simple session manager

Super simple bash script to manage graphical sessions on linux and other unix systems

# Usage

move the script to a directory in your $PATH and create a .ssm directory in your home directory

inside the .ssm directory you can place scripts that executes a graphical session

**Note:** the script files must end with the extension .session

examples of valid scripts:

**xfce4.session**
```bash
#!/bin/sh
startxfce4
```

**sway.session**
```bash
#!/bin/sh

export XDG_CURRENT_DESKTOP=Sway
export TERM=foot

exec dbus-run-session sway
```

Now you can put these lines in your shell profile configuration:

```bash
if [ -z "$DISPLAY" ] && [ "$(tty)" = "/dev/tty1" ]; then
exec ssm
fi
```

if you use bash than its `~/.bash_profile` and if you use zsh its `~/.zprofile`

now the next time you log in to your account it will appear a prompt to select the available sessions that you have created

if you have alredy launched a session with this script it will appear an option to launch the last session that you launched.
