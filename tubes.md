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