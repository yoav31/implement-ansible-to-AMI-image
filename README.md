# Implement Ansible Instead of AMI Images

This project demonstrates how to use Ansible to configure and manage AWS EC2 instances dynamically instead of relying on preconfigured AMI images. The infrastructure is managed using the AWS EC2 dynamic inventory plugin, and hosts are grouped automatically based on EC2 tags such as Service, Name, and Restart.

The goal is to allow new servers to be managed immediately after launch without rebuilding AMIs, making the system more flexible, scalable, and easier to maintain.

To run the main playbook and configure all relevant servers, use the following command:

ansible-playbook -i aws_ec2.yml site.yml --private-key /path/to/your-key.pem

To verify that the Nginx service is running correctly on servers tagged with Service=nginx, run:

ansible -i aws_ec2.yml service_nginx -m shell -a "systemctl status nginx" --private-key /path/to/your-key.pem -u ec2-user

To verify that the MySQL / MariaDB service is running correctly on servers tagged with Service=mysql, run:

ansible -i aws_ec2.yml service_mysql -m shell -a "systemctl status mariadb" --private-key /path/to/your-key.pem -u ec2-user

To verify that cron jobs were created successfully on all managed servers, run:

ansible -i aws_ec2.yml all -m shell -a "crontab -l" --private-key /path/to/your-key.pem -u ec2-user -b

This approach removes the need to rebuild AMI images for every configuration change and allows infrastructure behavior to be controlled entirely through code and instance metadata.
