# challenge7
/infra-repo
└── k8s/
    ├── k8s-secret.yaml        # Secret definition (optional)
    ├── secret-env-pod.yaml    # Pod using secrets as environment variables
    ├── secret-vol-pod.yaml    # Pod mounting secrets as volumes (optional)
    └── README.md              # This file
    
Step 1 – Create Kubernetes Secret

Option 1 – Using kubectl:

kubectl create secret generic db-credentials \
  --from-literal=DB_USER=dbuser \
  --from-literal=DB_PASSWORD=dbpassword

kubectl get secrets
kubectl describe secret db-credentials

kubectl apply -f k8s-secret.yaml

Step 2 – Inject Secret as Environment Variables

kubectl apply -f secret-env-pod.yaml
kubectl get pods
kubectl exec -it secret-env-pod -- printenv | grep DB_

Step 3 – Inject Secret as Mounted Files 

kubectl apply -f secret-vol-pod.yaml
kubectl get pods
kubectl exec -it secret-vol-pod -- ls /etc/secrets
kubectl exec -it secret-vol-pod -- cat /etc/secrets/DB_USER
kubectl exec -it secret-vol-pod -- cat /etc/secrets/DB_PASSWORD




Done By SHOBANA V
