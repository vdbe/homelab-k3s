.POSIX:

env ?= "prod"

default: boot cluster

~/.ssh/id_ed25519:
	ssh-keygen -t ed25519 -f "$@"

boot: ~/.ssh/id_ed25519
	ansible-playbook \
		--inventory inventories/${env}.yml \
		-e 'ansible_user=ansible-user' \
		boot.yml

cluster:
	ansible-playbook \
		--inventory inventories/${env}.yml \
		cluster.yml

console:
	ansible-console \
		--inventory inventories/${env}.yml
