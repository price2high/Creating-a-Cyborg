# CYBORG DIARY

![Ubuntu](https://img.shields.io/badge/Ubuntu-20.04%2B-orange?logo=ubuntu)
![Ansible](https://img.shields.io/badge/Ansible-Automation-blue?logo=ansible)
![SSH](https://img.shields.io/badge/SSH-Configured-green?logo=openssh)
![License](https://img.shields.io/badge/license-MIT-brightgreen)

_This is the living logbook of the Linux Node Cluster project. Documenting every system check, glitch, breakthrough, and command like a true terminal cyborg._

---

## [Day 1] - Initial Cluster Planning  
**Date:** 2025-04-07

**Actions:**
- Decided to build a lightweight, flexible Linux node cluster.
- Chose Ubuntu 20.04 LTS for its stability.
- Outlined the repo structure and essential setup scripts.


**Thoughts:**
- Might explore both Docker Swarm and Kubernetes use cases.
- Need to plan for automated provisioning and health checks later.

---

## [Day 2] - SSH Configuration and Key Distribution  
**Date:** 2025-04-08

**Actions:**
- Created `ssh-keygen-setup.sh` for passwordless SSH access.
- Tested key-based login between master and two test nodes.

**Issues:**
- Encountered "Permission denied (publickey)" — fixed with correct permissions on `.ssh/authorized_keys`.

**Next:**
- Build Ansible inventory and common playbook.

---

## [Day 3] - Basic Ansible Setup  
**Date:** 2025-04-09

**Actions:**
- Wrote initial Ansible `playbook.yml` for package installation.
- Defined `common` role to standardize setup across nodes.

**Success:**
- Successfully ran playbook against all nodes using `hosts.ini`.

**Next:**
- Add cluster-specific tasks (e.g. Docker install or Kube init).

---

## [Day 4] - Firewall and Networking  
**Date:** 2025-04-10

**Actions:**
- Created `firewall-config.sh` to automate UFW setup.
- Opened cluster communication ports (2377, 7946, 4789).

**Notes:**
- Nodes can now ping and SSH into each other seamlessly.

---

## [Day 5] - Repo Polish and GitHub Prep  
**Date:** 2025-04-11

**Actions:**
- Finalized folder structure.
- Added `.gitignore`, `README.md`, and this `CYBORG_DIARY.md`.

**Reflections:**
- This repo is clean, automated, and reusable.
- Ready for deployment testing or Docker/Kubernetes integration.

---

> “Logs aren't just for debugging machines — they debug your mind.”
