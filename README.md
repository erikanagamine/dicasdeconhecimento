# Dicas de conhecimento

Todos os links mencionados aqui são links publicos e não tem relação com nenhum empregador que esteja atuando.

Aqui eu deixo alguns links para conhecimento no geral.

Eventos AWS:
- ReInvent: https://reinvent.awsevents.com/
- Eventos e Webinares: https://aws.amazon.com/pt/events/?events-master-main.sort-by=item.additionalFields.startDateTime&events-master-main.sort-order=desc&awsf.events-master-type=*all&awsf.events-master-audience=*all&awsf.events-master-level=*all
- Desconto em certificação (2022) Cloud Practitioner, Developer, Solutions Architect Associate: https://pages.awscloud.com/LATAM-launch-STR-aws-certification-disc-br-2022-interest.html

Caminhos de aprendizado (Learning Paths):
- https://aws.amazon.com/pt/training/learn-about/

Dados:
- Database Offerings: https://explore.skillbuilder.aws/learn/course/internal/view/elearning/61/aws-database-offerings
- Data Analytics: https://explore.skillbuilder.aws/learn/course/internal/view/elearning/44/data-analytics-fundamentals
- Data Analytics (português): https://explore.skillbuilder.aws/learn/course/external/view/elearning/570/data-analytics-fundamentals-portuguese


Technical Essentials / Cloud Practitioner Essentials:
-  Glossário da AWS: https://docs.aws.amazon.com/pt_br/general/latest/gr/glos-chap.html
- Treinamento sob demanda: https://explore.skillbuilder.aws/learn/course/external/view/elearning/8287/aws-cloud-practitioner-essentials-portuguese?sc_channel=em&sc_campaign=%7B%7Bprogram.name%7D%7D&traincert_AMER_FY21_Q4_tclever_FLE_EM=&sc_medium=em_%7B%7Bcampaign.id%7D%7D&sc_content=REG_la_traincert&sc_geo=latm&sc_country=br&sc_outcome=reg&trk=em_%7B%7Bcampaign.id%7D%7D
- Infraestrutura global: https://aws.amazon.com/pt/about-aws/global-infrastructure/
- Regiões: https://aws.amazon.com/pt/about-aws/global-infrastructure/regions_az/?p=ngi&loc=2
- Modelo de responsabilidade compartilhada: https://aws.amazon.com/compliance/shared-responsibility-model/
- VPC: https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html
- Purpose built databases: https://aws.amazon.com/products/databases/
- Planos de suporte AWS: https://aws.amazon.com/pt/premiumsupport/?nc=sn&loc=0
- EC2 Familias: https://aws.amazon.com/pt/ec2/instance-types/
- EC2 pricing options (definição de preço da EC2): https://aws.amazon.com/pt/ec2/pricing/?nc1=h_ls
- S3 Definição de preço: https://aws.amazon.com/pt/s3/pricing/
- Well Architect Framework: https://aws.amazon.com/pt/architecture/well-architected

Big Data:
- Kinesis: https://aws.amazon.com/pt/about-aws/whats-new/2021/11/amazon-kinesis-data-streams-on-demand/
- Kinesis: https://aws.amazon.com/blogs/aws/amazon-kinesis-data-streams-on-demand-stream-data-at-scale-without-managing-capacity/
- SQL ou NoSQL: https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SQLtoNoSQL.html
- Athena Federation: https://docs.aws.amazon.com/athena/latest/ug/connect-to-a-data-source.html
- Tuning Tips para Athena: https://aws.amazon.com/blogs/big-data/top-10-performance-tuning-tips-for-amazon-athena/
- Curso Redshift: https://explore.skillbuilder.aws/learn/course/external/view/elearning/1316/amazon-redshift-service-primer


Exames:
- Cloud Practitioner: https://aws.amazon.com/pt/certification/certified-cloud-practitioner/
- Visão geral - Antes de realizar a prova (contempla pedido de extensão): https://aws.amazon.com/pt/certification/policies/before-testing/
- AWS Certification Official Practice Question Sets: https://explore.skillbuilder.aws/learn/course/external/view/elearning/9153/aws-certification-official-practice-question-sets-english
- AWS Certification Official Practice Question Sets (Português): https://explore.skillbuilder.aws/learn/course/internal/view/elearning/9161/aws-certification-official-practice-question-sets-portuguese-brazil
- AWS Cloud Practitioner Exam Rediness: https://explore.skillbuilder.aws/learn/course/internal/view/elearning/9449/exam-prep-aws-certified-cloud-practitioner-foundations
- Exame readiness Architect Associate: https://explore.skillbuilder.aws/learn/course/view/elearning/1037/exam-readiness-aws-certified-solutions-architect-associate-digital-portuguese

Referencia de clientes:
- Referencias de clientes: https://aws.amazon.com/pt/solutions/case-studies/?customer-references-cards.sort-by=item.additionalFields.sortDate&customer-references-cards.sort-order=desc&awsf.customer-references-location=*all&awsf.customer-references-segment=*all&awsf.customer-references-industry=*all&awsf.customer-references-use-case=*all&awsf.customer-references-tech-category=*all&awsf.customer-references-product=*all

Audio nas sessões
- (GTW) Se você teve problemas com o audio, pode consultar esse link: https://support.goto.com/meeting/help/why-cant-i-hear-anyone-g2m050056
- (Webex) https://help.webex.com/en-us/article/WBX12581/Webex-Audio-Troubleshooting


Demonstrações:
- EC2 user data: https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/user-data.html
- Workshops: https://workshops.aws/

Amazon linux:
```
#!/bin/bash


sudo yum install -y https://s3.us-west-2.amazonaws.com/amazon-ssm-us-west-2/latest/linux_amd64/amazon-ssm-agent.rpm
sudo yum install -y amazon-efs-utils
sudo systemctl status amazon-ssm-agent
sudo systemctl enable amazon-ssm-agent
sudo systemctl start amazon-ssm-agent
sudo systemctl status amazon-ssm-agent

sudo mkdir /efs
sudo chown ec2-user:ec2-user /efs

yum update -y amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2
yum install -y httpd mariadb-server
systemctl start httpd
systemctl enable httpd
usermod -a -G apache ec2-user
chown -R ec2-user:apache /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} \;
find /var/www -type f -exec chmod 0664 {} \;
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php

## Sam  - Serveless Application Model - Framework
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -a -G docker ec2-user

cd /tmp
wget https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip
unzip aws-sam-cli-linux-x86_64.zip -d sam-installation
sudo ./sam-installation/install

### others
sudo yum install -y git



```

Ubuntu:
```
#!/bin/bash

sudo apt-get update -y 
sudo apt-get install zip sed wget -y
sudo apt-get install amazon-efs-utils -y
sudo snap install amazon-ssm-agent --classic

sudo systemctl start snap.amazon-ssm-agent.amazon-ssm-agent.service
sudo systemctl stop snap.amazon-ssm-agent.amazon-ssm-agent.service
sudo systemctl status snap.amazon-ssm-agent.amazon-ssm-agent.service
sudo snap start amazon-ssm-agent

sudo mkdir /efs
sudo chown ubuntu:ubuntu /efs
sudo apt-get install npm -y
sudo apt-get install node* -y

sudo apt-get install -y httpd mariadb-server
systemctl start httpd
systemctl enable httpd
usermod -a -G apache ec2-user
chown -R ec2-user:apache /var/www
chmod 2775 /var/www
find /var/www -type d -exec chmod 2775 {} \;
find /var/www -type f -exec chmod 0664 {} \;
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php

```
Para o Systems Manager (Não esquecer): "How to access Quick Setup
To access this capability, choose Quick Setup in the navigation pane of the Systems Manager console. To access the Organization Quick Setup type, which you can use to target multiple accounts and Regions, sign in to the management account for your organization before accessing Quick Setup. For more information, see Getting started with AWS Organizations in the AWS Organizations User Guide." fonte: https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-quick-setup.html#quick-setup-instance-profile


Campanhas globais:
- Cloud Practitioner: https://pages.awscloud.com/GLOBAL-ln-GC-TrainCert-Cloud-Practitioner-Challenge-2022-reg.html?trk=711adc9b-e1af-49cf-a767-1c0ebfa2a8da&sc_channel=em
- Pagina de eventos de eventos: https://pages.awscloud.com/LATAM-ln-OE-br-virtual-events-pm-2022-reg-event.html?trk=dc404d02-8dda-4ee1-b8af-310c16eef4d6&sc_channel=el
- revisão do exame - Cloud Practitioner: https://explore.skillbuilder.aws/learn/course/external/view/elearning/13566/exam-prep-aws-certified-cloud-practitioner-with-practice-material-amazon-portuguese


