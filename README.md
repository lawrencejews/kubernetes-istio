## Kubernetes & Istio with Google Cloud
This project showcases docker, kubernetes, istio, grafana, prometheus, gitops, google kubernetes engine, argocd and kiali.
#### Docker
- Install a java version that matches your OS and validate.
- Downloads for Amazon Corretto 17:`https://docs.aws.amazon.com/corretto/latest/corretto-17-ug/downloads-list.html` OR configure your java environment.
- Add permissions for the project and `chmod +x gradlew` Build the java binary with `./gradlew clean bootJar`.
- Build the image `docker build --tag devops-blue:1.0.0 .`
- RUN the image: `docker run -d -p 8888:8111 --name my-devops-blue devops-blue:1.0.0`.
- Access created application `http://localhost:8888/devops/blue/swagger-ui/index.html`.
- Tag to docker repo: `docker tag devops-blue:1.0.0 [your-username]/devops-blue:1.0.0`.
- Push to Docker hub: `docker push [your-username]/devops-blue:1.0.0`.
- Remove the container used in the hands-on `docker ps -a` then `docker rm -f my-devops-blue`.
- Clean out the images `docker images rm -f [image ID]`.
#### Kubernetes
- Make sure you have `minikube installed` and started `minikube start` before creating a deployment.
- Create a deployment on kubernetes with the image `kubectl create deployment my-devops-blue --image [your-username]/devops-blue:1.0.0`.
- Expose the service `kubectl expose deployment my-devops-blue --type LoadBalancer --port 8111 --name my-devops-blue-lb`.
- Create a tunnel for the service in another tab for minikube `minikube tunnel`.
- Scaling up the deployment `kubectl scale deployment my-devops-blue --replicas=3`.
- Delete deployment `kubectl delete deployment my-devops-blue`.