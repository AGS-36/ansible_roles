# Домашнее задание к занятию "09.04 Jenkins"

## Подготовка к выполнению

1. Создать 2 VM: для jenkins-master и jenkins-agent.
2. Установить jenkins при помощи playbook'a.
3. Запустить и проверить работоспособность.
4. Сделать первоначальную настройку.

## Основная часть

1. Сделать Freestyle Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
```
Started by user netologytest
Running as SYSTEM
Building remotely on node-1 in workspace /opt/jenkins_agent/workspace/molecule
The recommended git tool is: NONE
using credential git
 > git rev-parse --resolve-git-dir /opt/jenkins_agent/workspace/molecule/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/AGS-36/ansible_roles.git # timeout=10
Fetching upstream changes from https://github.com/AGS-36/ansible_roles.git
 > git --version # timeout=10
 > git --version # 'git version 1.8.3.1'
using GIT_SSH to set credentials git_key
[INFO] Currently running in a labeled security context
[INFO] Currently SELinux is 'enforcing' on the host
 > /usr/bin/chcon --type=ssh_home_t /opt/jenkins_agent/workspace/molecule@tmp/jenkins-gitclient-ssh16532116821190805312.key
Verifying host key using known hosts file
You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist, please go to 'Manage Jenkins' -> 'Configure Global Security' -> 'Git Host Key Verification Configuration' and configure host key verification.
 > git fetch --tags --progress https://github.com/AGS-36/ansible_roles.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision fa81a4cf1972a4303f1edc5263d779e16045a27c (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f fa81a4cf1972a4303f1edc5263d779e16045a27c # timeout=10
Commit message: "Create requirements.txt"
 > git rev-list --no-walk fa81a4cf1972a4303f1edc5263d779e16045a27c # timeout=10
[molecule] $ /bin/sh -xe /tmp/jenkins8515264781488790011.sh
+ cd vector_1
+ pip3 install -r requirements.txt
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: selinux in /usr/local/lib/python3.6/site-packages (from -r requirements.txt (line 1)) (0.2.1)
Requirement already satisfied: ansible-lint==5.1.3 in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 2)) (5.1.3)
Requirement already satisfied: yamllint==1.26.3 in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 3)) (1.26.3)
Requirement already satisfied: lxml in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 4)) (4.9.1)
Requirement already satisfied: molecule==3.4.0 in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 5)) (3.4.0)
Requirement already satisfied: molecule_docker in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 6)) (1.1.0)
Requirement already satisfied: jmespath in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 7)) (0.10.0)
Requirement already satisfied: ruamel.yaml<1,>=0.15.34 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (0.17.21)
Requirement already satisfied: wcmatch>=7.0 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (8.3)
Requirement already satisfied: pyyaml in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (5.4.1)
Requirement already satisfied: packaging in /usr/local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (21.3)
Requirement already satisfied: rich>=9.5.1 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (12.5.1)
Requirement already satisfied: typing-extensions in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (4.1.1)
Requirement already satisfied: enrich>=1.2.6 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (1.2.7)
Requirement already satisfied: tenacity in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (8.0.1)
Requirement already satisfied: pathspec>=0.5.3 in /home/jenkins/.local/lib/python3.6/site-packages (from yamllint==1.26.3->-r requirements.txt (line 3)) (0.9.0)
Requirement already satisfied: setuptools in /usr/local/lib/python3.6/site-packages (from yamllint==1.26.3->-r requirements.txt (line 3)) (59.6.0)
Requirement already satisfied: pluggy<1.0,>=0.7.1 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.13.1)
Requirement already satisfied: cerberus!=1.3.3,!=1.3.4,>=1.3.1 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (1.3.2)
Requirement already satisfied: subprocess-tee>=0.3.2 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.3.5)
Requirement already satisfied: cookiecutter>=1.7.3 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (1.7.3)
Requirement already satisfied: dataclasses in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.8)
Requirement already satisfied: paramiko<3,>=2.5.0 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (2.11.0)
Requirement already satisfied: Jinja2>=2.11.3 in /usr/local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (3.0.3)
Requirement already satisfied: click-help-colors>=0.9 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.9.1)
Requirement already satisfied: click<9,>=8.0 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (8.0.4)
Requirement already satisfied: distro>=1.3.0 in /usr/local/lib/python3.6/site-packages (from selinux->-r requirements.txt (line 1)) (1.7.0)
Requirement already satisfied: requests in /home/jenkins/.local/lib/python3.6/site-packages (from molecule_docker->-r requirements.txt (line 6)) (2.27.1)
Requirement already satisfied: docker>=4.3.1 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule_docker->-r requirements.txt (line 6)) (5.0.3)
Requirement already satisfied: ansible-compat>=0.5.0 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule_docker->-r requirements.txt (line 6)) (1.0.0)
Requirement already satisfied: cached-property~=1.5 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-compat>=0.5.0->molecule_docker->-r requirements.txt (line 6)) (1.5.2)
Requirement already satisfied: importlib-metadata in /home/jenkins/.local/lib/python3.6/site-packages (from click<9,>=8.0->molecule==3.4.0->-r requirements.txt (line 5)) (4.8.3)
Requirement already satisfied: jinja2-time>=0.2.0 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (0.2.0)
Requirement already satisfied: python-slugify>=4.0.0 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (6.1.2)
Requirement already satisfied: poyo>=0.5.0 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (0.5.0)
Requirement already satisfied: six>=1.10 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (1.16.0)
Requirement already satisfied: binaryornot>=0.4.4 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (0.4.4)
Requirement already satisfied: websocket-client>=0.32.0 in /home/jenkins/.local/lib/python3.6/site-packages (from docker>=4.3.1->molecule_docker->-r requirements.txt (line 6)) (1.3.1)
Requirement already satisfied: MarkupSafe>=2.0 in /usr/local/lib64/python3.6/site-packages (from Jinja2>=2.11.3->molecule==3.4.0->-r requirements.txt (line 5)) (2.0.1)
Requirement already satisfied: pynacl>=1.0.1 in /home/jenkins/.local/lib/python3.6/site-packages (from paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (1.5.0)
Requirement already satisfied: bcrypt>=3.1.3 in /home/jenkins/.local/lib/python3.6/site-packages (from paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (4.0.0)
Requirement already satisfied: cryptography>=2.5 in /usr/local/lib64/python3.6/site-packages (from paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (38.0.1)
Requirement already satisfied: idna<4,>=2.5 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (3.3)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (1.26.12)
Requirement already satisfied: charset-normalizer~=2.0.0 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (2.0.12)
Requirement already satisfied: certifi>=2017.4.17 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (2022.6.15.1)
Requirement already satisfied: commonmark<0.10.0,>=0.9.0 in /home/jenkins/.local/lib/python3.6/site-packages (from rich>=9.5.1->ansible-lint==5.1.3->-r requirements.txt (line 2)) (0.9.1)
Requirement already satisfied: pygments<3.0.0,>=2.6.0 in /home/jenkins/.local/lib/python3.6/site-packages (from rich>=9.5.1->ansible-lint==5.1.3->-r requirements.txt (line 2)) (2.13.0)
Requirement already satisfied: ruamel.yaml.clib>=0.2.6 in /home/jenkins/.local/lib/python3.6/site-packages (from ruamel.yaml<1,>=0.15.34->ansible-lint==5.1.3->-r requirements.txt (line 2)) (0.2.6)
Requirement already satisfied: bracex>=2.1.1 in /home/jenkins/.local/lib/python3.6/site-packages (from wcmatch>=7.0->ansible-lint==5.1.3->-r requirements.txt (line 2)) (2.2.1)
Requirement already satisfied: pyparsing!=3.0.5,>=2.0.2 in /usr/local/lib/python3.6/site-packages (from packaging->ansible-lint==5.1.3->-r requirements.txt (line 2)) (3.0.9)
Requirement already satisfied: chardet>=3.0.2 in /home/jenkins/.local/lib/python3.6/site-packages (from binaryornot>=0.4.4->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (5.0.0)
Requirement already satisfied: cffi>=1.12 in /usr/local/lib64/python3.6/site-packages (from cryptography>=2.5->paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (1.15.1)
Requirement already satisfied: zipp>=0.5 in /home/jenkins/.local/lib/python3.6/site-packages (from importlib-metadata->click<9,>=8.0->molecule==3.4.0->-r requirements.txt (line 5)) (3.6.0)
Requirement already satisfied: arrow in /home/jenkins/.local/lib/python3.6/site-packages (from jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (1.2.3)
Requirement already satisfied: text-unidecode>=1.3 in /home/jenkins/.local/lib/python3.6/site-packages (from python-slugify>=4.0.0->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (1.3)
Requirement already satisfied: pycparser in /usr/local/lib/python3.6/site-packages (from cffi>=1.12->cryptography>=2.5->paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (2.21)
Requirement already satisfied: python-dateutil>=2.7.0 in /home/jenkins/.local/lib/python3.6/site-packages (from arrow->jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (2.8.2)
+ molecule test
/home/jenkins/.local/lib/python3.6/site-packages/requests/__init__.py:104: RequestsDependencyWarning: urllib3 (1.26.12) or chardet (5.0.0)/charset_normalizer (2.0.12) doesn't match a supported version!
  RequestsDependencyWarning)
INFO     default scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun...
INFO     Guessed /opt/jenkins_agent/workspace/molecule as project root directory
WARNING  Computed fully qualified role name of Artem.vector_1 does not follow current galaxy requirements.
Please edit meta/main.yml and assure we can correctly determine full role name:

galaxy_info:
role_name: my_name  # if absent directory name hosting role is used instead
namespace: my_galaxy_namespace  # if absent, author is used instead

Namespace: https://galaxy.ansible.com/docs/contributing/namespaces.html#galaxy-namespace-limitations
Role: https://galaxy.ansible.com/docs/contributing/creating_role.html#role-names

As an alternative, you can add 'role-name' to either skip_list or warn_list.

INFO     Using /home/jenkins/.cache/ansible-lint/d4f4df/roles/Artem.vector_1 symlink to current repository in order to enable Ansible to find the role using its expected full name.
INFO     Added ANSIBLE_ROLES_PATH=~/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles:/home/jenkins/.cache/ansible-lint/d4f4df/roles
INFO     Running default > dependency
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
INFO     Running ansible-galaxy collection install --force -v community.docker:>=1.9.1
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
WARNING  Skipping, missing the requirements file.
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
WARNING  Skipping, missing the requirements file.
INFO     Running default > lint
INFO     Lint is disabled.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
INFO     Sanity checks: 'docker'
/home/jenkins/.local/lib/python3.6/site-packages/paramiko/transport.py:33: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.hazmat.backends import default_backend
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Wait for instance(s) deletion to complete] *******************************
ok: [localhost] => (item=instance_1)
ok: [localhost] => (item=instance_2)

TASK [Delete docker networks(s)] ***********************************************

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Running default > syntax

playbook: /opt/jenkins_agent/workspace/molecule/vector_1/molecule/default/converge.yml
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
INFO     Running default > create
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17

PLAY [Create] ******************************************************************

TASK [Log into a Docker registry] **********************************************
skipping: [localhost] => (item=None)
skipping: [localhost] => (item=None)
skipping: [localhost]

TASK [Check presence of custom Dockerfiles] ************************************
ok: [localhost] => (item={'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True})
ok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True})

TASK [Create Dockerfiles from image names] *************************************
skipping: [localhost] => (item={'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True})
skipping: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True})

TASK [Discover local Docker images] ********************************************
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'item': {'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 0, 'ansible_index_var': 'i'})
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'item': {'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 1, 'ansible_index_var': 'i'})

TASK [Build an Ansible compatible image (new)] *********************************
skipping: [localhost] => (item=molecule_local/docker.io/pycontribs/debian)
skipping: [localhost] => (item=molecule_local/docker.io/pycontribs/ubuntu)

TASK [Create docker network(s)] ************************************************

TASK [Determine the CMD directives] ********************************************
ok: [localhost] => (item={'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True})
ok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True})

TASK [Create molecule instance(s)] *********************************************
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Wait for instance(s) creation to complete] *******************************
FAILED - RETRYING: Wait for instance(s) creation to complete (300 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (299 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (298 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (297 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (296 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (295 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (294 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (293 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (292 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (291 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (290 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (289 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (288 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (287 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (286 retries left).
FAILED - RETRYING: Wait for instance(s) creation to complete (285 retries left).
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '455645851612.4020', 'results_file': '/home/jenkins/.ansible_async/455645851612.4020', 'changed': True, 'failed': False, 'item': {'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True}, 'ansible_loop_var': 'item'})
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '684119128359.4049', 'results_file': '/home/jenkins/.ansible_async/684119128359.4049', 'changed': True, 'failed': False, 'item': {'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=5    changed=2    unreachable=0    failed=0    skipped=4    rescued=0    ignored=0

INFO     Running default > prepare
WARNING  Skipping, prepare playbook not configured.
INFO     Running default > converge

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_2]
ok: [instance_1]

TASK [Include vector_1] ********************************************************

TASK [vector_1 : Get vector distrib] *******************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_1]
changed: [instance_2]

TASK [vector_1 : Install vector packages] **************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_1]
changed: [instance_2]

TASK [vector_1 : Template a file to /etc/vector/] ******************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_2]
changed: [instance_1]

PLAY RECAP *********************************************************************
instance_1                 : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance_2                 : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running default > idempotence

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_2]
ok: [instance_1]

TASK [Include vector_1] ********************************************************

TASK [vector_1 : Get vector distrib] *******************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_2]
ok: [instance_1]

TASK [vector_1 : Install vector packages] **************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1]
ok: [instance_2]

TASK [vector_1 : Template a file to /etc/vector/] ******************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1]
ok: [instance_2]

PLAY RECAP *********************************************************************
instance_1                 : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance_2                 : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Idempotence completed successfully.
INFO     Running default > side_effect
WARNING  Skipping, side effect playbook not configured.
INFO     Running default > verify
INFO     Running Ansible Verifier

PLAY [Verify] ******************************************************************

TASK [Example assertion] *******************************************************
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1] => {
    "changed": false,
    "msg": "All assertions passed"
}
ok: [instance_2] => {
    "changed": false,
    "msg": "All assertions passed"
}

TASK [Check config] ************************************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_2]
changed: [instance_1]

PLAY RECAP *********************************************************************
instance_1                 : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance_2                 : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Verifier completed successfully.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: Wait for instance(s) deletion to complete (300 retries left).
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Delete docker networks(s)] ***********************************************

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Pruning extra files from scenario ephemeral directory
Finished: SUCCESS
```
2. Сделать Declarative Pipeline Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
```
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps{
                git branch: 'master', url: 'https://github.com/AGS-36/ansible_roles.git'
            }
        }
        stage('Install molecule') {
            steps{
                sh 'cd vector_1; ls; pip3 install -r requirements.txt'
                sh "echo =============="
            }
        }
        stage('Run Molecule'){
            steps{
                sh 'cd vector_1; molecule test'
            }
        }
    }
}
```
3. Перенести Declarative Pipeline в репозиторий в файл `Jenkinsfile`.
https://github.com/AGS-36/ansible_roles/blob/master/Jenkinsfile
4. Создать Multibranch Pipeline на запуск `Jenkinsfile` из репозитория.
```
Branch indexing
18:43:44 Connecting to https://api.github.com with no credentials, anonymous access
18:43:45 Jenkins-Imposed API Limiter: Current quota for Github API usage has 52 remaining (1 over budget). Next quota of 60 in 59 min. Sleeping for 5 min 24 sec.
18:43:45 Jenkins is attempting to evenly distribute GitHub API requests. To configure a different rate limiting strategy, such as having Jenkins restrict GitHub API requests only when near or above the GitHub rate limit, go to "GitHub API usage" under "Configure System" in the Jenkins settings.
18:46:46 Jenkins-Imposed API Limiter: Still sleeping, now only 2 min 22 sec remaining.
Obtained Jenkinsfile from 02e92213d912aedd1d288178835508348cf6ad4b
[Pipeline] Start of Pipeline
[Pipeline] node
Running on node-1 in /opt/jenkins_agent/workspace/multi_master
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning with configured refspecs honoured and without tags
Cloning repository https://github.com/AGS-36/ansible_roles.git
 > git init /opt/jenkins_agent/workspace/multi_master # timeout=10
Fetching upstream changes from https://github.com/AGS-36/ansible_roles.git
 > git --version # timeout=10
 > git --version # 'git version 1.8.3.1'
 > git fetch --no-tags --progress https://github.com/AGS-36/ansible_roles.git +refs/heads/master:refs/remotes/origin/master # timeout=10
Avoid second fetch
Checking out Revision 02e92213d912aedd1d288178835508348cf6ad4b (master)
 > git config remote.origin.url https://github.com/AGS-36/ansible_roles.git # timeout=10
 > git config --add remote.origin.fetch +refs/heads/master:refs/remotes/origin/master # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 02e92213d912aedd1d288178835508348cf6ad4b # timeout=10
Commit message: "Create Jenkinsfile"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Checkout)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
Fetching changes from the remote Git repository
Checking out Revision 02e92213d912aedd1d288178835508348cf6ad4b (refs/remotes/origin/master)
Commit message: "Create Jenkinsfile"
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Install molecule)
[Pipeline] sh
 > git rev-parse --resolve-git-dir /opt/jenkins_agent/workspace/multi_master/.git # timeout=10
 > git config remote.origin.url https://github.com/AGS-36/ansible_roles.git # timeout=10
Fetching upstream changes from https://github.com/AGS-36/ansible_roles.git
 > git --version # timeout=10
 > git --version # 'git version 1.8.3.1'
 > git fetch --tags --progress https://github.com/AGS-36/ansible_roles.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 02e92213d912aedd1d288178835508348cf6ad4b # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git checkout -b master 02e92213d912aedd1d288178835508348cf6ad4b # timeout=10
+ cd vector_1
+ ls
defaults
handlers
meta
molecule
README.md
requirements.txt
tasks
templates
tests
vars
+ pip3 install -r requirements.txt
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: selinux in /usr/local/lib/python3.6/site-packages (from -r requirements.txt (line 1)) (0.2.1)
Requirement already satisfied: ansible-lint==5.1.3 in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 2)) (5.1.3)
Requirement already satisfied: yamllint==1.26.3 in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 3)) (1.26.3)
Requirement already satisfied: lxml in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 4)) (4.9.1)
Requirement already satisfied: molecule==3.4.0 in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 5)) (3.4.0)
Requirement already satisfied: molecule_docker in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 6)) (1.1.0)
Requirement already satisfied: jmespath in /home/jenkins/.local/lib/python3.6/site-packages (from -r requirements.txt (line 7)) (0.10.0)
Requirement already satisfied: packaging in /usr/local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (21.3)
Requirement already satisfied: tenacity in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (8.0.1)
Requirement already satisfied: pyyaml in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (5.4.1)
Requirement already satisfied: typing-extensions in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (4.1.1)
Requirement already satisfied: rich>=9.5.1 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (12.5.1)
Requirement already satisfied: wcmatch>=7.0 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (8.3)
Requirement already satisfied: enrich>=1.2.6 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (1.2.7)
Requirement already satisfied: ruamel.yaml<1,>=0.15.34 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-lint==5.1.3->-r requirements.txt (line 2)) (0.17.21)
Requirement already satisfied: pathspec>=0.5.3 in /home/jenkins/.local/lib/python3.6/site-packages (from yamllint==1.26.3->-r requirements.txt (line 3)) (0.9.0)
Requirement already satisfied: setuptools in /usr/local/lib/python3.6/site-packages (from yamllint==1.26.3->-r requirements.txt (line 3)) (59.6.0)
Requirement already satisfied: dataclasses in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.8)
Requirement already satisfied: cookiecutter>=1.7.3 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (1.7.3)
Requirement already satisfied: paramiko<3,>=2.5.0 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (2.11.0)
Requirement already satisfied: pluggy<1.0,>=0.7.1 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.13.1)
Requirement already satisfied: cerberus!=1.3.3,!=1.3.4,>=1.3.1 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (1.3.2)
Requirement already satisfied: subprocess-tee>=0.3.2 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.3.5)
Requirement already satisfied: click<9,>=8.0 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (8.0.4)
Requirement already satisfied: Jinja2>=2.11.3 in /usr/local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (3.0.3)
Requirement already satisfied: click-help-colors>=0.9 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule==3.4.0->-r requirements.txt (line 5)) (0.9.1)
Requirement already satisfied: distro>=1.3.0 in /usr/local/lib/python3.6/site-packages (from selinux->-r requirements.txt (line 1)) (1.7.0)
Requirement already satisfied: ansible-compat>=0.5.0 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule_docker->-r requirements.txt (line 6)) (1.0.0)
Requirement already satisfied: docker>=4.3.1 in /home/jenkins/.local/lib/python3.6/site-packages (from molecule_docker->-r requirements.txt (line 6)) (5.0.3)
Requirement already satisfied: requests in /home/jenkins/.local/lib/python3.6/site-packages (from molecule_docker->-r requirements.txt (line 6)) (2.27.1)
Requirement already satisfied: cached-property~=1.5 in /home/jenkins/.local/lib/python3.6/site-packages (from ansible-compat>=0.5.0->molecule_docker->-r requirements.txt (line 6)) (1.5.2)
Requirement already satisfied: importlib-metadata in /home/jenkins/.local/lib/python3.6/site-packages (from click<9,>=8.0->molecule==3.4.0->-r requirements.txt (line 5)) (4.8.3)
Requirement already satisfied: poyo>=0.5.0 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (0.5.0)
Requirement already satisfied: python-slugify>=4.0.0 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (6.1.2)
Requirement already satisfied: jinja2-time>=0.2.0 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (0.2.0)
Requirement already satisfied: binaryornot>=0.4.4 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (0.4.4)
Requirement already satisfied: six>=1.10 in /home/jenkins/.local/lib/python3.6/site-packages (from cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (1.16.0)
Requirement already satisfied: websocket-client>=0.32.0 in /home/jenkins/.local/lib/python3.6/site-packages (from docker>=4.3.1->molecule_docker->-r requirements.txt (line 6)) (1.3.1)
Requirement already satisfied: MarkupSafe>=2.0 in /usr/local/lib64/python3.6/site-packages (from Jinja2>=2.11.3->molecule==3.4.0->-r requirements.txt (line 5)) (2.0.1)
Requirement already satisfied: pynacl>=1.0.1 in /home/jenkins/.local/lib/python3.6/site-packages (from paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (1.5.0)
Requirement already satisfied: bcrypt>=3.1.3 in /home/jenkins/.local/lib/python3.6/site-packages (from paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (4.0.0)
Requirement already satisfied: cryptography>=2.5 in /usr/local/lib64/python3.6/site-packages (from paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (38.0.1)
Requirement already satisfied: charset-normalizer~=2.0.0 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (2.0.12)
Requirement already satisfied: certifi>=2017.4.17 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (2022.6.15.1)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (1.26.12)
Requirement already satisfied: idna<4,>=2.5 in /home/jenkins/.local/lib/python3.6/site-packages (from requests->molecule_docker->-r requirements.txt (line 6)) (3.3)
Requirement already satisfied: commonmark<0.10.0,>=0.9.0 in /home/jenkins/.local/lib/python3.6/site-packages (from rich>=9.5.1->ansible-lint==5.1.3->-r requirements.txt (line 2)) (0.9.1)
Requirement already satisfied: pygments<3.0.0,>=2.6.0 in /home/jenkins/.local/lib/python3.6/site-packages (from rich>=9.5.1->ansible-lint==5.1.3->-r requirements.txt (line 2)) (2.13.0)
Requirement already satisfied: ruamel.yaml.clib>=0.2.6 in /home/jenkins/.local/lib/python3.6/site-packages (from ruamel.yaml<1,>=0.15.34->ansible-lint==5.1.3->-r requirements.txt (line 2)) (0.2.6)
Requirement already satisfied: bracex>=2.1.1 in /home/jenkins/.local/lib/python3.6/site-packages (from wcmatch>=7.0->ansible-lint==5.1.3->-r requirements.txt (line 2)) (2.2.1)
Requirement already satisfied: pyparsing!=3.0.5,>=2.0.2 in /usr/local/lib/python3.6/site-packages (from packaging->ansible-lint==5.1.3->-r requirements.txt (line 2)) (3.0.9)
Requirement already satisfied: chardet>=3.0.2 in /home/jenkins/.local/lib/python3.6/site-packages (from binaryornot>=0.4.4->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (5.0.0)
Requirement already satisfied: cffi>=1.12 in /usr/local/lib64/python3.6/site-packages (from cryptography>=2.5->paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (1.15.1)
Requirement already satisfied: zipp>=0.5 in /home/jenkins/.local/lib/python3.6/site-packages (from importlib-metadata->click<9,>=8.0->molecule==3.4.0->-r requirements.txt (line 5)) (3.6.0)
Requirement already satisfied: arrow in /home/jenkins/.local/lib/python3.6/site-packages (from jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (1.2.3)
Requirement already satisfied: text-unidecode>=1.3 in /home/jenkins/.local/lib/python3.6/site-packages (from python-slugify>=4.0.0->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (1.3)
Requirement already satisfied: pycparser in /usr/local/lib/python3.6/site-packages (from cffi>=1.12->cryptography>=2.5->paramiko<3,>=2.5.0->molecule==3.4.0->-r requirements.txt (line 5)) (2.21)
Requirement already satisfied: python-dateutil>=2.7.0 in /home/jenkins/.local/lib/python3.6/site-packages (from arrow->jinja2-time>=0.2.0->cookiecutter>=1.7.3->molecule==3.4.0->-r requirements.txt (line 5)) (2.8.2)
[Pipeline] sh
+ echo ==============
==============
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Run Molecule)
[Pipeline] sh
+ cd vector_1
+ molecule test
/home/jenkins/.local/lib/python3.6/site-packages/requests/__init__.py:104: RequestsDependencyWarning: urllib3 (1.26.12) or chardet (5.0.0)/charset_normalizer (2.0.12) doesn't match a supported version!
  RequestsDependencyWarning)
INFO     default scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun...
INFO     Guessed /opt/jenkins_agent/workspace/multi_master as project root directory
WARNING  Computed fully qualified role name of Artem.vector_1 does not follow current galaxy requirements.
Please edit meta/main.yml and assure we can correctly determine full role name:

galaxy_info:
role_name: my_name  # if absent directory name hosting role is used instead
namespace: my_galaxy_namespace  # if absent, author is used instead

Namespace: https://galaxy.ansible.com/docs/contributing/namespaces.html#galaxy-namespace-limitations
Role: https://galaxy.ansible.com/docs/contributing/creating_role.html#role-names

As an alternative, you can add 'role-name' to either skip_list or warn_list.

INFO     Using /home/jenkins/.cache/ansible-lint/b08118/roles/Artem.vector_1 symlink to current repository in order to enable Ansible to find the role using its expected full name.
INFO     Added ANSIBLE_ROLES_PATH=~/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles:/home/jenkins/.cache/ansible-lint/b08118/roles
INFO     Running default > dependency
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
WARNING  Skipping, missing the requirements file.
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
WARNING  Skipping, missing the requirements file.
INFO     Running default > lint
INFO     Lint is disabled.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
INFO     Sanity checks: 'docker'
/home/jenkins/.local/lib/python3.6/site-packages/paramiko/transport.py:33: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.hazmat.backends import default_backend
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Wait for instance(s) deletion to complete] *******************************
ok: [localhost] => (item=instance_1)
ok: [localhost] => (item=instance_2)

TASK [Delete docker networks(s)] ***********************************************

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Running default > syntax

playbook: /opt/jenkins_agent/workspace/multi_master/vector_1/molecule/default/converge.yml
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
INFO     Running default > create
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17

PLAY [Create] ******************************************************************

TASK [Log into a Docker registry] **********************************************
skipping: [localhost] => (item=None)
skipping: [localhost] => (item=None)
skipping: [localhost]

TASK [Check presence of custom Dockerfiles] ************************************
ok: [localhost] => (item={'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True})
ok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True})

TASK [Create Dockerfiles from image names] *************************************
skipping: [localhost] => (item={'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True})
skipping: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True})

TASK [Discover local Docker images] ********************************************
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'item': {'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 0, 'ansible_index_var': 'i'})
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'item': {'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 1, 'ansible_index_var': 'i'})

TASK [Build an Ansible compatible image (new)] *********************************
skipping: [localhost] => (item=molecule_local/docker.io/pycontribs/debian)
skipping: [localhost] => (item=molecule_local/docker.io/pycontribs/ubuntu)

TASK [Create docker network(s)] ************************************************

TASK [Determine the CMD directives] ********************************************
ok: [localhost] => (item={'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True})
ok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True})

TASK [Create molecule instance(s)] *********************************************
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Wait for instance(s) creation to complete] *******************************
FAILED - RETRYING: Wait for instance(s) creation to complete (300 retries left).
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '883008680588.3617', 'results_file': '/home/jenkins/.ansible_async/883008680588.3617', 'changed': True, 'failed': False, 'item': {'image': 'docker.io/pycontribs/debian', 'name': 'instance_1', 'pre_build_image': True}, 'ansible_loop_var': 'item'})
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '457569615457.3647', 'results_file': '/home/jenkins/.ansible_async/457569615457.3647', 'changed': True, 'failed': False, 'item': {'image': 'docker.io/pycontribs/ubuntu', 'name': 'instance_2', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=5    changed=2    unreachable=0    failed=0    skipped=4    rescued=0    ignored=0

INFO     Running default > prepare
WARNING  Skipping, prepare playbook not configured.
INFO     Running default > converge

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1]
ok: [instance_2]

TASK [Include vector_1] ********************************************************

TASK [vector_1 : Get vector distrib] *******************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_1]
changed: [instance_2]

TASK [vector_1 : Install vector packages] **************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_1]
changed: [instance_2]

TASK [vector_1 : Template a file to /etc/vector/] ******************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_1]
changed: [instance_2]

PLAY RECAP *********************************************************************
instance_1                 : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance_2                 : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running default > idempotence

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1]
ok: [instance_2]

TASK [Include vector_1] ********************************************************

TASK [vector_1 : Get vector distrib] *******************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_2]
ok: [instance_1]

TASK [vector_1 : Install vector packages] **************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1]
ok: [instance_2]

TASK [vector_1 : Template a file to /etc/vector/] ******************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1]
ok: [instance_2]

PLAY RECAP *********************************************************************
instance_1                 : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance_2                 : ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Idempotence completed successfully.
INFO     Running default > side_effect
WARNING  Skipping, side effect playbook not configured.
INFO     Running default > verify
INFO     Running Ansible Verifier

PLAY [Verify] ******************************************************************

TASK [Example assertion] *******************************************************
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_1] => {
    "changed": false,
    "msg": "All assertions passed"
}
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
ok: [instance_2] => {
    "changed": false,
    "msg": "All assertions passed"
}

TASK [Check config] ************************************************************
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
[WARNING]: Collection community.docker does not support Ansible version 2.10.17
changed: [instance_2]
changed: [instance_1]

PLAY RECAP *********************************************************************
instance_1                 : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
instance_2                 : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Verifier completed successfully.
INFO     Running default > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running default > destroy
/usr/local/lib/python3.6/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography and will be removed in a future release.
  from cryptography.exceptions import InvalidSignature
[WARNING]: Collection community.docker does not support Ansible version 2.10.17

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: Wait for instance(s) deletion to complete (300 retries left).
changed: [localhost] => (item=instance_1)
changed: [localhost] => (item=instance_2)

TASK [Delete docker networks(s)] ***********************************************

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     Pruning extra files from scenario ephemeral directory
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

5. Создать Scripted Pipeline, наполнить его скриптом из [pipeline](./pipeline).
6. Внести необходимые изменения, чтобы Pipeline запускал `ansible-playbook` без флагов `--check --diff`, если не установлен параметр при запуске джобы (prod_run = True), по умолчанию параметр имеет значение False и запускает прогон с флагами `--check --diff`.
```
node("linux"){
    stage("Git checkout"){
        git credentialsId: '5ac0095d-0185-431b-94da-09a0ad9b0e2c', url: 'git@github.com:aragastmatb/example-playbook.git'
    }
    stage("Sample define secret_check"){
        secret_check=true
    }
    stage("Run playbook"){
        if (secret_check){
            sh 'ansible-playbook site.yml -i inventory/prod.yml'
        }
        else{
            sh 'ansible-playbook site.yml -i inventory/prod.yml --check --diff'
        }

    }
}
```
7. Проверить работоспособность, исправить ошибки, исправленный Pipeline вложить в репозиторий в файл `ScriptedJenkinsfile`.
8. Отправить ссылку на репозиторий с ролью и Declarative Pipeline и Scripted Pipeline.

