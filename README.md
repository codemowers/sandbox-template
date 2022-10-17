kubectl -n argocd create secret generic gitea-codemowers-labs \
  --from-literal=type=git \
  --from-literal=url=git@git.k-space.ee:codemowers/lab-template \
  --from-file=sshPrivateKey=id_ecdsa
kubectl label -n argocd secret gitea-kube argocd.argoproj.io/secret-type=repository



kubectl create secret generic -n playground-laurivosandi traefik-forward-auth-secrets \
    --from-literal=SECRET=$(cat /dev/urandom | base64 | head -c 30)

    

kubectl delete secret -n default drone-secrets
 kubectl create secret generic -n default drone-secrets \
    --from-literal=DRONE_GITHUB_CLIENT_ID=bc47fae63733a290d8a8 \
    --from-literal=DRONE_GITHUB_CLIENT_SECRET=521d45b1e337b344c8f3b9fa1eec6deb02843e4b \
    --from-literal=DRONE_RPC_SECRET=$(cat /dev/urandom | base64 | head -c 30)

