-t, --tag stringArray               Name and optionally a tag (format: "name:tag")
`docker build -t python_sshd .`

-d, --detach                         Run container in background and print container ID
`docker run -d python_sshd`

ensure ssh service is started
`ansible myhosts -i inventory.ini  -m ansible.builtin.service -a "name=ssh state=started"`