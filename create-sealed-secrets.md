
1) generate new passwords
https://www.random.org/passwords/?num=4&len=24&format=plain&rnd=new

2) create secret
kubectl create secret generic kutu-postgres-secret \
--dry-run \
--from-literal=adminpassword='secret1' \
--from-literal=user='secret2' \
--from-literal=kutusecret='secret3' \
--from-literal=password='secret4' \
-o yaml >mysecret.yaml

login with oc login, set curent project.

follow instructions from here
https://github.com/baloise-incubator/okd4-cluster-infra-apps/tree/master/sealed-secrets

/c/dev/kubeseal --namespace=kutuapp-test --cert https://raw.githubusercontent.com/baloise-incubator/okd4-cluster-infra-apps/master/sealed-secrets/kubeseal.crt  -oyaml <mysecret.yaml >mysealedsecret.yaml

