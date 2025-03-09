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


