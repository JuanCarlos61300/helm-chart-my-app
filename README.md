#my-app
Chart de Helm con frontend, backend y base de datos PostgreSQL con disco persistente. Cada parte es un subchart en `charts/`.

#instalar
Desarrollo:
    helm install juan-dev . -f values-dev.yaml -n dev --create-namespace
Producción crear antes el Secret con la contraseña de la base de datos
    kubectl create namespace prod
    kubectl create secret generic juan-db-credentials \
      --from-literal=POSTGRES_PASSWORD='<contraseña>' -n prod
    helm install juan-prod . -f values-prod.yaml -n prod

#configurar
Todo se cambia en `values.yaml`, `values-dev.yaml` o `values-prod.yaml`, sin tocar las plantillas.
#desinstalar
    helm uninstall juan-dev -n dev
