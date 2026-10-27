# Laboratorio pratico de Kubernetes

Execucao real em GitHub Codespaces em 27/10/2026.

## Arquivos
- deployment.yaml: configuracao inicial com 2 replicas, nginx:1.27 e recursos definidos.
- service.yaml: Service NodePort 30080.

## Etapas executadas
1. minikube start --driver=docker --memory=2048 --cpus=2
2. kubectl get nodes e kubectl cluster-info
3. kubectl apply -f deployment.yaml e verificacao de 2 Pods Running
4. kubectl apply -f service.yaml
5. kubectl port-forward service/minha-app-service 8080:80 e teste HTTP 200
6. kubectl scale deployment minha-app --replicas=4
7. Ajuste no YAML para 4 replicas e nginx:1.28; kubectl apply e rollout status
8. kubectl rollout undo deployment/minha-app; 4 replicas novamente em nginx:1.27
9. Exclusao do Service e Deployment; minikube stop

## Ajuste do ambiente
Falha de DNS dentro do Minikube impedia o download do kindnet. A imagem indicada pelo DaemonSet e as imagens nginx:1.27 e nginx:1.28 foram baixadas no Docker do host e importadas com minikube image load. O Pod do kindnet foi recriado, e o no ficou Ready.

Os manifests deste repositorio foram restaurados para a configuracao inicial, permitindo repetir o exercicio. Os prints de cada etapa foram salvos para entrega no AVA.
