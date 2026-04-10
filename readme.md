# Demo Helm Chart

Chart Helm simples usado como exemplo para interface rancher.

## Estrutura
- `templates/deployment.yaml`: cria o Deployment da aplicacao
- `templates/service.yaml`: expoe a aplicacao internamente no cluster
- `templates/ingress.yaml`: cria o Ingress - opcional
- `values.yaml`: define os valores padrao do chart
- `questions.yaml`: define os campos exibidos na rancher para configuracao

## Valores principais
- `replicaCount`: quantidade de replicas da aplicacao
- `image.repository`: repositorio da imagem do container
- `image.tag`: tag da imagem utilizada no deploy
- `service.type`: tipo do Service Kubernetes
- `service.port`: porta exposta pela aplicacao
- `ingress.enabled`: habilita ou desabilita a criacao do Ingress

## Instalacao
```bash
helm upgrade --install demo ./rancher-ui \
  --namespace demo --create-namespace
```

## Exemplo de override
```bash
helm upgrade --install demo-app ./rancher-ui \
  --namespace demo --create-namespace \
  --set image.repository=nginx \
  --set image.tag=alguma \
  --set service.port=8080 \
  --set ingress.enabled=true \
  --set ingress.hosts[0].host=demo.com.br
```
