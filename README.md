# ansible-bioxgem

## Create User with Conda Setup

### Prerequisites

Ensure your `~/.ssh/config` includes the remote server configuration (with ProxyJump if needed):

```config
Host your_server_name
    HostName your.server.com
    User your_username
    ProxyJump proxy_host
```

### Usage

**Option 1: Using SSH config (one-off)**
```bash
ansible-playbook create_user.yml -kK -i "your_server_name,"
```

**Option 2: Using inventory file**

Create `inventory`:
```
your_server_name ansible_user=your_username
```

Run:
```bash
ansible-playbook create_user.yml -kK -i inventory
```

### Flags
- `-k` — SSH password prompt (required for both ProxyJump hops)
- `-K` — sudo password prompt

### Variables
- `user_name` — Username to create
- `user_password` — Password for the new user
