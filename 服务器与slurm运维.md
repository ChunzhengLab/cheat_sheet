```bash
#列出节点信息
sinfo 

#重启某个节点
#in node
systemctl status slurmd.service
systemctl start slurmd.service
systemctl restart slurmd.service
systemctl enable slurmd.service

#重启slurm服务
#in root
systemctl status slurmctld
systemctl start slurmctld
systemctl restart slurmctld
systemctl enable slurmctld

#恢复某个节点
scontrol update NodeName=node2 State=RESUME
```
