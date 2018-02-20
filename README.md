# ansible_yum-update

I think it is awkward to update the vulnerability detected by Vuls by logging in to the server every time. So I registered servers managed by ansible and updated it with one shot.

# Vulnerability Update Method

1.Describe the middleware you want to update to group_vars / all   

When a vulnerability is detected, first of all middleware is written in group_vars / all. In /roles/updates/tasks/main.yml, with_items is being used and assigned.

# Caution
If there is a blank value, yum update - y will be executed and all will be updated.  
Please delete unnecessary [- ""] and then let it flow.  

# Dryrun/Run

The part of updates is skiping, but do not worry as it is the shell module specification.  

When specifying a host, you need to specify it from the hosts directory when you enter a command.  
You can specify only one host that you want to update with [-l host name].  

```
$ ansible-playbook - privile - key = (key) - i hosts / (env) - u (user) vuls - update.yml - check
```
```
$ ansible-playbook -private-key = (key) -i hosts / (env) -u (user) -l (host) vuls-update.yml --check
```
