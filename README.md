# k8spoc

Taking the earlier DockerPOC and adding k8s / helm in to the mix:  
https://github.com/jeromeza/dockerpoc

This allows us to deploy a helm chart to k8s which contains:
- deployment
- service
- ingress
- HPA (horizontal pod autoscaling)

The relevant resources are then created and a website is added to the pod/s via the gitlab-ci.yml values specified:

$FQDN:  
blog.example.com

$IMAGE:  
webdevops/php-apache:5.6    
webdevops/php-apache:7.0   
webdevops/php-apache:7.1   
webdevops/php-apache:7.2   
webdevops/php-apache:7.3   
webdevops/php-apache:7.4   

$REPO  
https://github.com/jeromeza/blog.example.com.git

You can also stress test your cluster and the HPA component:

```watch -n1 "kubectl get hpa ; echo ; kubectl get deployment ; echo ; kubectl get pod ; echo ; kubectl top pod"```
```kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c 'echo "192.168.2.9 blog.example.com" >> /etc/hosts; while sleep 0.01 ; do wget -q -O- http://blog.example.com:8081/funwithmath.php; done'```
