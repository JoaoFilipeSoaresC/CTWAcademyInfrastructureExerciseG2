# CTWAcademyInfrastructureExerciseG2

Group Assignment:
Create a terraform and ansible code to deploy an instance and install the Prometheus stack on it. The instance type should be "Standard_D4_v3". Your prometheus instance should be able to connect to the instance with the public IP 20.218.85.149 and gather its node exporter metrics, presenting them in a grafana dashboard.

This is a group assignment, each group must deliver their code in their prefered form (share git repository url, zip file sent via email, etc...) before July 21 at 17:00.

Individual questions:

1 - What modification should be done to the terraform code in order to deploy three virtual machines instead of one?

In order to deploy 3 VMs instead of one, it's necessary to add a count=3 on the Terraform main file. This count=3 needs to be applied in different places:

- along with the network interface creation
- along with the network management disk creation
- along with the virtual machines creation

In order to create unique names, count.index is used. For example, if we nominate our VM vm-ctw-g2, what will happen is the first VM will be named vm-ctw-g2$1, the second one will be named vm-ctw-g2$2, and so on.


2 - During the group assignment, various files will have to be downloaded from the internet (the prometheus stack binaries), is there a way for ansible to be sure that these files are the originals and have not been tampered with?




3 - What is metric scraping?

Metric scraping is a metric treatment method where Prometheus receives metrics on the node exporters.
However, Prometheus is the one that makes the metrics request, not the node exporter itself, which decides to when to send them, even without a request being made.
