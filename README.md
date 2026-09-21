# ansible

1. Log into the App Store

2. Install `command line tools`

```bash
xcode-select --install
```

3. Install Xcode through the App Store

4. Agree to the license

```bash
sudo xcodebuild -license
```

5. Run the bootstrap script

```bash
curl https://raw.githubusercontent.com/UNRULYEON/ansible/main/bootstrap-mac | bash
```

https://blog.vandenbrand.org/2016/01/04/how-to-automate-your-mac-os-x-setup-with-ansible/

https://github.com/wayofdev/ansible-role-mac-cfg

## Linting

GitHub Actions runs three checks at each push and pull request
(`.github/workflows/lint.yml`). They find broken YAML, an unknown module and a
bad playbook structure before you run the playbook on a Mac. They do not
replace a run on a real device.

To run the same checks on your machine:

```bash
pip install -r requirements-dev.txt
ansible-galaxy install -r requirements.yml

yamllint .
ansible-playbook main.yml --syntax-check
ansible-lint
```

`ansible-lint` also reports warnings that do not fail the build. They are
listed in the `warn_list` of `.ansible-lint`.
