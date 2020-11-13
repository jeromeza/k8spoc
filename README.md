# k8spoc

Taking the earlier DockerPOC and adding k8s / helm in to the mix:  
https://github.com/jeromeza/dockerpoc

This allows us to deploy a helm chart to k8s which contains:
- deployment
- service
- ingress
- hpa

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
