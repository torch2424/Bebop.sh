# Bebop.sh
Useful Functions for Writing Scripts fast, with Good UX

# How to include/install in your script

### Download and include in project

This is the reccomended way to include bebop in your bash scripting libraries. Especially for things like a bash based CLI to run certain commands, or setup. The only caveat of this method, is that you will not have the latest bebop version. So check back for new features for this. Since you are not losing anything by not building on un-created features / unexpected changes. And with this method, you can ensure your users your stamp of approval of bebop security and things (not that bebop is doing anything threatening of course).

[Download the latest bebop.sh](https://raw.githubusercontent.com/torch2424/bebop.sh/master/bebop.sh)

Include the following

```
# Import bebop.sh
source project_dir/bebop.sh
```

### Download on runtime (Convienient, least reccomended) 

This will download the script to a temp file, and then source so that you have access to `bebop.sh`. Please note the following gotchas:

* Downloading and running a script from the internet is dangerous. You should always review scripts before your run them on your machine.

* If bebop is going to be a dependency, I'd highly reccomend you do not do this, as users should not be comfortable with this. And if you still decide to, please put in bold big letters and encourage your readers to read through bebop as well. For development, I'd think this would be okay, as long as you do the first method and review bebop.sh before moving into user's hands. And I would suggest the **Prefer remote bebop, Fallback to local bebop** method over simply using this one

* This will require an internet connection everytime your run the script. This is under the assumption you are running the script in a subshell, `./` or `bash`, and not attempting to source the script

```
# Import of bebop.sh
# https://github.com/torch2424/bebop.sh
BEBOP_URL="https://raw.githubusercontent.com/torch2424/bebop.sh/master/bebop.sh"; if curl -o /dev/null -sIf "$BEBOP_URL"; then curl -s "$BEBOP_URL" -o /tmp/bebop.sh; source /tmp/bebop.sh; else echo "Could not load bebop from $BEBOP_URL. Please check your internet connection. Halting execution of the script..."; exit 1; fi;
```

### Prefer local bebop, Falback to remote bebop (not reccomended)

TBD

### Prefer remote bebop, Fallback to local bebop (not reccomended)

This will attemp the download on runtime option, and if not availbe, will use a locally installed bebop. This is good for developing alongside bebop changes, and is not reccomended to releasing to users.

**NOTE:** Please be sure to place your path of bebop.sh inside of the `BEBOP_PATH="";` variable. e.g `BEBOP_PATH="$HOME/bebop.sh";`

```
# Import of bebop.sh
# https://github.com/torch2424/bebop.sh
BEBOP_PATH="$HOME/.files_libs/bebop.sh"; BEBOP_URL="https://raw.githubusercontent.com/torch2424/bebop.sh/master/bebop.sh"; if [ -f "$BEBOP_PATH" ]; then source "$BEBOP_PATH"; elif curl -o /dev/null -sIf "$BEBOP_URL"; then curl -s "$BEBOP_URL" -o /tmp/bebop.sh; source /tmp/bebop.sh; else echo "Could not load bebop from $BEBOP_PATH or $BEBOP_URL. Please check your bebop path and internet connection. Halting execution of the script..."; exit 1; fi;
```
