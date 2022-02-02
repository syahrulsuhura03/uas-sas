Install Ansible untuk hosts ubuntu server

```markdown
sudo apt install ansible sshpass
```

Buat directory

```markdown
mkdir -p ~/ansible/tubes
```

Buat lxc_db_server, lxc_php5_1, lxc_php5_2, lxc_php7_1, lxc_php7_2, lxc_php7_3, lxc_php7_4, lxc_php7_5 and lxc_php7_6

```markdown
lxc-create -n lxc_db_server -t download -- --dist debian --release buster --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php5_1 -t download -- --dist debian --release buster --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php5_2 -t download -- --dist debian --release buster --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php7_1 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php7_2 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php7_3 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php7_4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php7_5 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-create -n lxc_php7_6 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
lxc-start -n lxc_db_server
lxc-start -n lxc_php5_1 
lxc_start -n lxc_php5_2
lxc-start -n lxc_php7_1 
lxc_start -n lxc_php7_2
lxc_start -n lxc_php7_3
lxc_start -n lxc_php7_4
lxc_start -n lxc_php7_5
lxc_start -n lxc_php7_6
apt update; apt upgrade -y; apt install -y nano
```

setting menjadi auto start

```markdown
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_db_server/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php5_1/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php5_2/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php7_1/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php7_2/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php7_3/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php7_4/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php7_5/config
echo "lxc.start.auto = 1" >> /var/lib/lxc/lxc_php7_6/config
```

setting ip static tiap containers

![WhatsApp Image 2022-02-02 at 2 05 53 PM](https://user-images.githubusercontent.com/93044506/152105332-dabe174a-41d6-4cec-af4e-4db55ff68411.jpeg)



![WhatsApp Image 2022-02-02 at 2 06 28 PM](https://user-images.githubusercontent.com/93044506/152105340-b93a0ecd-8961-4d67-8854-a2ba16d4a3fb.jpeg)

setting hosts dan menambahkan ip 

```markdown
nano /etc/hosts
```

![WhatsApp Image 2022-02-02 at 2 36 53 PM](https://user-images.githubusercontent.com/93044506/152106000-0d74e4bb-b014-44ed-a079-ee9561d96b87.jpeg)



install ssh server

```markdown
apt install openssh-server
```

![WhatsApp Image 2022-02-02 at 2 44 19 PM](https://user-images.githubusercontent.com/93044506/152106876-d95ebbd1-a4cb-4855-8375-5c0c985c7ed7.jpeg)



setting 

```markdown
nano /etc/ssh/sshd_config

# setting config
PermitRootLogin yes
RSAAuthentication yes
```

![WhatsApp Image 2022-02-02 at 2 47 03 PM](https://user-images.githubusercontent.com/93044506/152106880-1fb76fd1-8146-4a3d-85d6-f8eb3142b053.jpeg)

kemudian restart ssh

```markdown
service sshd restart
```

setting passowrd tiap containers

```markdown
passwd (ex: 1)
```

![WhatsApp Image 2022-02-02 at 3 17 13 PM](https://user-images.githubusercontent.com/93044506/152111406-e25073cd-9d72-4758-9ac3-31f6ad2536c7.jpeg)

kemudian masuk ke directory

```markdown
cd ~/ansible/tubes
```

buat hosts dan menambahkan script

![WhatsApp Image 2022-02-02 at 3 41 51 PM](https://user-images.githubusercontent.com/93044506/152113425-03d40d3c-4c7e-477b-bd2f-9a6d55be192a.jpeg)