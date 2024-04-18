# All those misfits

## proxychains - speed up SOCKS proxy scanning with nmap
https://www.hackwhackandsmack.com/?p=1021
```
seq 1 1000 | xargs -P 50 -I{} proxychains nmap -p {} -sT -Pn --open -n -T4 --min-parallelism 100 --min-rate 1 <target_ip> > <outfile|proxychains_nmap.txt>
```

## mount - share with kerberos ticket (should be in /tmp/krb5cc_0)
```
sudo mount -t cifs -o sec=krb5,vers=3.0 '//SERVER.DOMAIN.LOCAL/SHARE' /mnt/share
```
## autorecon - scan single target
```
autorecon --single-target -o <output_folder> <target_ip>
```

## vagrant - start machine
```
vagrant up <machine>
```

## vagrant - halt machine
```
vagrant halt <machine>
```

## vagrant - reload machine
```
vagrant reload <machine>
```

## ansible - run playbook with inventory file
```
ansible-playbook -i <inventory_file|inventory> <playbook|main.yml>
```

## ansible - list available collections
```
ansible-galaxy collection list
```

## WebDAV - run WebDAV server with Python
#platform/linux #target/local #cat/OSCP
```
sudo wsgidav --host=0.0.0.0 --port=<port|80> --auth=anonymous --root <path|/home/kali/PandorasBox/tmp>
```

## swaks - send email with swaks
#platform/linux #target/remote #cat/OSCP
```
sudo swaks -t <email_to> --from <email_from> --attach @<attachment|config.library-ms> --server <target_ip> --body @<body|body.txt> --header <Subject|"Subject: Mail Server Update"> --suppress-data -ap 
```

## DonPAPI - 
```
papi --hashes <LM|0000000000000000>:<NT> -local_auth <user|Administrator>@<target_ip>
```

## Imagemagick - convert image size
```
convert <image> -resize <x|300>x<y|300> <out>
```

## Windows - install .msi file
```
msiexec /quiet /qn /i <msi_path>
```

## Windows - pipe winPEAS output to file
```
./peas.exe | tee-object -filepath peas.txt
```

## Linux - pipe linPEAS output to file
```
./linpeas.sh | tee peas.txt
```