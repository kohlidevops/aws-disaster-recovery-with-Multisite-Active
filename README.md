# aws-disaster-recovery-with-Multisite-Active

Consider a large enterprise with data centers in different geographical regions. In a multi-site disaster recovery strategy, you have active and synchronized environments running in multiple AWS regions. For instance, your primary application might be running in the US-West region, and an exact replica of the application is running in the US-East region. In case of a disaster in one region, traffic can be redirected to the healthy region, ensuring minimal disruption.

Before start this method, Please deploy workloads using below link

https://github.com/kohlidevops/aws-disaster-recovery/blob/main/README.md

https://github.com/kohlidevops/aws-disaster-recovery-with-backup-restore-/blob/main/README.md

https://github.com/kohlidevops/aws-disaster-recovery-with-region-outage/blob/main/README.md

https://github.com/kohlidevops/aws-disaster-recovery-with-Pilot-Light/blob/main/README.md

https://github.com/kohlidevops/aws-disaster-recovery-with-Warm-Standby/blob/main/README.md

Make ensure to remove the NULL SG and add ALB SG from/to Mumbai Region Load balancer.

Remove the secondary CNAME record from Route53 – that is NVirginia Load balancer mapped CNAME.

Update the primary CNAME record from Route 53.

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/3d304fec-27b4-4ee5-bac2-52b7f7ac2a12)

**Create one more Health check for NVirginia Region Load balancer**

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/0ed8325a-cc8d-4c5f-b504-c56adeb2c9fc)

**To create CNAME record for NVirginia Region Load balancer**

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/68d071bb-63db-456f-b9f4-574b115f483f)

You can check the health check for both NVirginia and Mumbai region

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/ab63103d-8963-4791-a4fa-33f4727d867d)

As of now, I’m getting Mumbai region application. Because this region is very close to me.

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/54a7947d-2d1e-4c08-894d-dd3ecd0c60a8)

I have added some data through Mumbai and NVirginia application.

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/89bd554f-613a-4951-9100-5b04b3897883)

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/c6545b8c-a729-4973-a7cd-5ab39e1b83c7)

Now I’m going to make Mumbai region as Outage with the help of NULL Security group. So All of my request should redirect to NVirginia region with the help of Latency algorithm.

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/6e519eea-327c-4b81-8959-ebc5ea18010e)

My all request has been sent to NVirginia Load balancer. All data's are up to date.

![image](https://github.com/kohlidevops/aws-disaster-recovery-with-Multisite-Active/assets/100069489/bbf0aabe-659a-4c9d-a77d-c878f9a969d8)

That's it.









