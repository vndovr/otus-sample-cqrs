helm install my-kf bitnami/kafka

helm install my-pg-auth -f postgres-auth.yaml bitnami/postgresql
helm install my-pg-order -f postgres-order.yaml bitnami/postgresql
helm install my-pg-event -f postgres-event.yaml bitnami/postgresql

helm install my-auth -f otus-sample-auth.yaml ./otus-sample-auth
helm install my-order -f otus-sample-order.yaml ./otus-sample-order
helm install my-event -f otus-sample-event.yaml ./otus-sample-event

helm install my-ing1 -f otus-sample-ing.yaml ./otus-sample-ing1
helm install my-ing2 -f otus-sample-ing.yaml ./otus-sample-ing2

newman run Otus-6.postman_collection.json -e Otus6.postman_environment.json --delay-request 100

helm uninstall my-ing1
helm uninstall my-ing2
helm uninstall my-event
helm uninstall my-order
helm uninstall my-auth
helm uninstall my-pg-event
helm uninstall my-pg-order
helm uninstall my-pg-auth
helm uninstall my-kf
