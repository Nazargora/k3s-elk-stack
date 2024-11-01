kubectl get secret es-elk-es-elastic-user -n elk -o jsonpath="{.data.elastic}" | base64 --decode
kubectl logs -n kube-system -l app.kubernetes.io/name=traefik -f
kubectl create secret tls kibana.demoapps.win   --cert=/etc/letsencrypt/live/TEST.COM/fullchain.pem   --key=/etc/letsencrypt/live/demoapps.win/privkey.pem   -n elk
kubectl create -f https://download.elastic.co/downloads/eck/2.14.0/crds.yaml  # https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-eck.html
kubectl apply -f https://download.elastic.co/downloads/eck/2.14.0/operator.yaml
curl -sfL https://get.k3s.io | sh - # allow create masterand worker node in one vm
kubectl exec -n elk watchguard-firebox-log-udp -- /bin/bash -c "kill -SIGHUP 1" 
