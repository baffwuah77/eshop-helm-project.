# eShop Helm Project

Helm chart that deploys the eShop microservice application
(ui, catalog, carts, checkout, orders, assets + MySQL, DynamoDB, Redis, RabbitMQ)
to Kubernetes. Includes per-environment values for dev, test, preprod and prod.

## Deploy (minikube)

    helm upgrade --install eshop ./eshop -n dev --create-namespace \
      -f eshop/values-dev.yaml -f eshop/values-lowmem.yaml
    kubectl port-forward svc/ui 8080:80 -n dev

Open http://localhost:8080

Other environments: use values-test.yaml, values-preprod.yaml or values-prod.yaml
and pass real passwords with --set secrets.mysqlPassword=... (never commit them).
