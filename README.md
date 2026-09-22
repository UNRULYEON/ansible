# ansible

Sets up a Mac with my apps and settings.

## Set up a new Mac

1. Sign in to the App Store. The playbook installs App Store apps with `mas`, and `mas` cannot sign in for you.

2. Run the bootstrap script. It installs Homebrew (with the Xcode Command Line Tools) and Ansible, runs the playbook, and then reboots the Mac.

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/UNRULYEON/ansible/main/bootstrap-mac)"
```

To use a different branch, set `BRANCH`:

```bash
BRANCH=macos-27 bash -c "$(curl -fsSL https://raw.githubusercontent.com/UNRULYEON/ansible/macos-27/bootstrap-mac)"
```

## Run the playbook again

```bash
ansible-galaxy install -r requirements.yml
ansible-playbook main.yml --ask-become-pass
```

Add `--check --diff` for a dry run that shows what changes, without changing anything.

## Check for drift

Run `./drift` to compare the apps on this Mac with the playbook.

## Test on a clean Mac

`./test-vm` runs `bootstrap-mac` in a clean macOS 27 VM with [Tart](https://tart.run), waits for the reboot, and runs the playbook again to check that nothing changes. It tests the last commit on the current branch and skips the App Store apps. The first run downloads a ~31 GB image and needs about 60 GB of free space.

## Links

- https://blog.vandenbrand.org/2016/01/04/how-to-automate-your-mac-os-x-setup-with-ansible/
- https://github.com/wayofdev/ansible-role-mac-cfg
