# linux-troubleshootiing runbook

### Environment Basis

1. uname -a

![alt text](image.png)

2. lsb_release -a

![alt text](image-1.png)

### file system sanity

1. mkdir /tmp/runbook-demo, cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo

![alt text](image-2.png)

### Snapshot: CPU & Memory

1. top

![alt text](image-3.png)

2. ps -o pid

![alt text](image-4.png)

### Disk /IO

1. df -h 

![alt text](image-5.png)

2. du -sh
![alt text](image-6.png)

### Networks
 
1. ss -tulpn

![alt text](image-7.png)

2. netstat -tulpn

![alt text](image-8.png)

### Logs

1. journalctl -u docker -n 50

![alt text](image-9.png)

2. tail -n 50 auth.log

![alt text](image-10.png)