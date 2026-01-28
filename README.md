# Implement Ansible Instead of AMI Images

This project demonstrates how to use **Ansible** to configure and manage AWS EC2 instances dynamically instead of relying on preconfigured AMI images.

The infrastructure is managed using the **AWS EC2 dynamic inventory plugin**, and instances are grouped automatically based on EC2 tags such as `Service`, `Name`, and `Restart`.

This approach allows new servers to be managed immediately after launch, without rebuilding AMIs, making the system more flexible, scalable, and easier to maintain.

---

## Prerequisites

- AWS EC2 instances with proper IAM permissions
- Ansible installed
- `amazon.aws` collection installed
- SSH access using a `.pem` key
- EC2 instances tagged correctly (e.g. `Service=nginx`, `Service=mysql`)

---

## Run the main playbook

Configure all relevant servers using the dynamic inventory:

```bash
ansible-playbook -i aws_ec2.yml site.yml \
  --private-key /path/to/your-key.pem


