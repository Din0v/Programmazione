# Come usare Zram in Fedora 

1. Vedere se è montato
``` bash  
lsblk 
```
![[Pasted image 20230604113228.png]]

2. oppure usare il commando 
```bash 
   zramctl
```
![[Pasted image 20230604113305.png]]

3. anche questo:
```bash
swapon --show
```
![[Pasted image 20230604113354.png]]

4. per diattivare lo swap basta usare questo commando come superuser
```bash 
sudo swapoff -a 
```

![[Pasted image 20230604113444.png]]


what did i do to disable this permanently? 

```bash 
sudo dnf remove zram-generator-defaults
```

how to bring it back ? easy reverse the previous command 

```bash 
sudo dnf install zram-generator-defaults
```

---
