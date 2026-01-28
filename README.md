# implement ansible to AMI image
implement ansible to manage new servers instead of an AMI image.


run command:  ansible-playbook -i aws_ec2.yml site.yml --private-key **your pem file**

nginx cheack:  ansible -i aws_ec2.yml service_nginx -m shell -a "systemctl status nginx" --private-key **your pem file** -u ec2-user
mysql cheack:  ansible -i aws_ec2.yml service_mysql -m shell -a "systemctl status mariadb" --private-key **your pem file** -u ec2-user
Cron cheack:   ansible -i aws_ec2.yml all -m shell -a "crontab -l" --private-key yoav.pem -u ec2-user -b
