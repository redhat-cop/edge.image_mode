# Edge Image_mode Collection

This repository contains the `edge.image_mode` Ansible Collection.

The collection relies on [fedora.linux\_system\_roles](https://galaxy.ansible.com/ui/repo/published/fedora/linux_system_roles/) or [redhat.rhel\_system\_roles](https://console.redhat.com/ansible/automation-hub/repo/published/redhat/rhel_system_roles/), as well as [containers.podman](https://galaxy.ansible.com/ui/repo/published/containers/podman/).

## External requirements

You will need a RHEL 9.5 (or higher) server to be used as builder host.
On this node you will need to have a user with SSH access and root capabilities, usable with an Ansible become method.

Furthermore you will need a container registry where you can push and pull images you'll create.

## Included content

The basic idea is to have a collection around Image Mode aka bootc, covering the following actions:

* Prepare a builder host where to build and convert bootc images
* Build a bootable container image based on a Containerfile and (content) files, using podman build
* Convert this image into a VM/HW image (qcow2, iso, etc) based on an optional blueprint, (other content) files and a configurable call to bootc-image-builder

The builder host shall be mostly stateless so that it doesn't need to be backed-up, and we assume the existence of a container registry.

> **NOTE:** the roles contain templates for Containerfile, Blueprint and the `bootc-image-builder` call, but those are only examples (to be extended), and templates local to the playbooks/Git repo could also be used.
The content files copied are also expected to be in the Git repo, next to the playbooks.

## Using this collection

```bash
    ansible-galaxy collection install edge.image_mode
```

You can also include it in a `requirements.yml` file and install it via `ansible-galaxy collection install -r requirements.yml` using the format:

```yaml
collections:
  - name: edge.image_mode
```

To upgrade the collection to the latest available version, run the following command:

```bash
ansible-galaxy collection install edge.image_mode --upgrade
```

You can also install a specific version of the collection, for example, if you need to downgrade when something is broken in the latest version (please report an issue in this repository). Use the following syntax where `X.Y.Z` can be any [available version](https://galaxy.ansible.com/edge/image_mode):

```bash
ansible-galaxy collection install edge.image_mode:==X.Y.Z
```

See [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more details.

## Release notes

See the [changelog](https://github.com/ansible-collections/edge.image_mode/tree/main/CHANGELOG.rst).

## Roadmap

<!-- Optional. Include the roadmap for this collection, and the proposed release/versioning strategy so users can anticipate the upgrade/update cycle. -->

## More information

<!-- List out where the user can find additional information, such as working group meeting times, slack/IRC channels, or documentation for the product this collection automates. At a minimum, link to: -->

- [Ansible Collection overview](https://github.com/ansible-collections/overview)
- [Ansible User guide](https://docs.ansible.com/ansible/devel/user_guide/index.html)
- [Ansible Developer guide](https://docs.ansible.com/ansible/devel/dev_guide/index.html)
- [Ansible Collections Checklist](https://github.com/ansible-collections/overview/blob/main/collection_requirements.rst)
- [Ansible Community code of conduct](https://docs.ansible.com/ansible/devel/community/code_of_conduct.html)
- [The Bullhorn (the Ansible Contributor newsletter)](https://docs.ansible.com/ansible/devel/community/communication.html#the-bullhorn)
- [News for Maintainers](https://github.com/ansible-collections/news-for-maintainers)

## Licensing

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.
