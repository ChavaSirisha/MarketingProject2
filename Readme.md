# This is read me file

steps:
1) EC2 instance - large
<!-- install docker - optional
containerization of microservices - optional
use docker compose and run the service - optional  -->
2) install terraform, kubectl
3) create S3 bucket and dynamo db for state mgmt
run main.tf(backend) from command line
4) create modules for VPC and EKS cluster
run main.tf from command line
5) execute below commands:
aws eks update-kubeconfig --region us-east-1 --name <<cluster-name>>
kubectl config current-context - to verify whether we are connecting to eks cluster 
kubectl get all - to check whether any services available
kubectl apply -f serviceaccount.yaml - to create service account. If we dont create any SA, default SA will be taken. we have mentioned this created SA in deployment files. 
kubectl apply -f complete-deploy.yaml (all services, deployments are defined in this yaml)
note: we can not access any service from internet because the type of service is clusterIp. So update
frontend service to load balancer type.
6) kubectl get svc | grep frontendproxy
kubectl edit svc opentelemetry-demo-frontendproxy - edit type to LoadBalancer and wait for 5 mins.




