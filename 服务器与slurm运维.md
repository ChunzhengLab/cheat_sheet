参考链接

https://napp.fudan.edu.cn/wiki/index.php/Pcfarm

https://slurm.schedmd.com/overview

https://hpc.pku.edu.cn/_book/


```bash
#管理员访问计算节点 
ssh node1(1到9共9个计算节点)
```

```bash
#列出节点信息
sinfo 
```

```bash
#重启某个节点
#in node
systemctl status slurmd.service
systemctl start slurmd.service
systemctl restart slurmd.service
systemctl enable slurmd.service
```

```bash
#重启slurm服务
#in root
systemctl status slurmctld
systemctl start slurmctld
systemctl restart slurmctld
systemctl enable slurmctld
```

```bash
#恢复某个节点
scontrol update NodeName=node2 State=RESUME
```
