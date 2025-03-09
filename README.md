# k8s-ingress

* Before creating the ingress controller we have to install the dependcies of the load balancer creation which will  create the lb automatically.

* By using the helm chart we are adding the package controller to our cluster 

* Application Load Balancer is a ingress controller in the aws.

* Request comes to ALB from ALB request goes to the ingress. From ingress requests goes to the service from service it will goes to the pod.

* This example created by using the host Based.


https://docs.aws.amazon.com/eks/latest/userguide/lbc-helm.html

* alb.ingress.kubernetes.io/scheme: internet-facing
*  alb.ingress.kubernetes.io/target-type: ip
*  alb.ingress.kubernetes.io/tags: Environment=dev,Team=test
*  alb.ingress.kubernetes.io/group.name: joindevops

*** For creation of load balancer controller ***

* 1. Add the eks-charts Helm chart repository.
```
helm repo add eks https://aws.github.io/eks-charts
```
* 2. Update your local repo to make sure that you have the most recent charts.

```
helm repo update eks
```
* 3. If you’re deploying the controller to Amazon EC2 nodes that have restricted access to the Amazon EC2 instance metadata service (IMDS), or if you’re deploying to Fargate or Amazon EKS Hybrid Nodes, then add the following flags to the helm command that follows:

--set region=region-code

--set vpcId=vpc-xxxxxxxx

Replace my-cluster with the name of your cluster. In the following command, aws-load-balancer-controller is the Kubernetes service account that you created in a previous step.

For more information about configuring the helm chart, see values.yaml on GitHub.
```
helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=my-cluster \
  --set serviceAccount.create=false \
  --set serviceAccount.name=aws-load-balancer-controller
```


