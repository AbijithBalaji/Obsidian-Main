[[Issues]] 
Ever felt frustrated trying to switch between different windows of the same Application in GNOME? Especially while working with multiple browser windows or text editors. By default, GNOME has the keybindings of `Alt+'` (back tick) to switch between windows of the same application. The traditional `Alt+ Tab` would typically switch between applications. This can be a big discomfort for users who are used to the traditional way of switching between Windows through `Alt+Tab` and alarming for new users migrating from  Windows or Mac OS to the superior Linux. 

After going through a lot of forums and proposed solutions, I found a simple and effective way to solve this and restore the `Alt+Tab` Functionality. Here is a step by step guide to fix this issue and make GNOME's window switching usable!

#### Step 1 - Assign Key Bindings
The first step is to configure `Alt+Tab` to work the way we expect and this can be done in two ways
1.  **Using GNOME Settings:**
- Go to **Settings>Keyboard>Keyboard Shortcuts>Switch Windows** 
- Assign Alt+Tab as shortcut 

![[Pasted image 20241203132732.png]]

2. **Using `dconf-editor`** 
You can install dconf-editor, a gui-tool for managing the dconf files of the system by using
```
apt install dconf-editor
```
**change `apt` to the package manager of your distro**

After installation:
- Open `dconf-editor`.
- Navigate to  `/org/gnome/desktop/wm/keybindings/`.
- Locate `switch-applications`.
- Uncheck "Use Default Value". 
- Add the following Custom Value and Apply.
```
['<Super>Tab']
```

![[Pasted image 20241203132630.png]]

- Locate `swithch-windows`
- Uncheck "Use Default Value" 
- Add the following Custom Value and Apply
```
['<Alt>Tab']
```

![[Pasted image 20241203135151.png]]

###### After this, try switching between windows using `Alt+Tab`. If it works only within the current workspace, proceed to Step 2.
#### Step 2 - Enable Window Switching Across All Workspaces
By default, GNOME restricts `Alt+Tab` to windows within the same workspace. To change this behavior:

1. **Using the Command Line (CLI):** 
Open the terminal and run the following command to disable workspace isolation:
```
gsettings set org.gnome.shell.window-switcher current-workspace-only false
```
Verify The changes `false`
```
gsettings get org.gnome.shell.app-switcher current-workspace-only
```

If the value is returned as `True`,  Try the next method which is using the `dconf-editor`

2. **By using dconf-editor**
- Open `dconf-editor`.
- Navigate to  `/org/gnome/shell/window-switcher/`. 
- Find `current-workspace-only` toggle.
- Disable it (set the boolean value to `false`).

![[Pasted image 20241203141145.png]]

Now, `Alt+Tab` should switch between all open windows, regardless of the workspace.
#### Conclusion

Restoring Alt+Tab to its expected functionality makes GNOME much more intuitive, especially for those transitioning from other operating systems. With just a few steps, you can streamline your workflow and focus on productivity without worrying about window management quirks.

If you found this guide helpful or have other GNOME customization tips, feel free to share your thoughts in the comments. Let’s make the Linux desktop experience even better—one tweak at a time!
