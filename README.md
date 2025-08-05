# istio-installation

```
# 1. Install Istio using IstioOperator
kubectl create namespace istio-system
istioctl install -f istio/istio-operator.yaml

# 2. Deploy Gateway API resources
kubectl apply -f gateway-api/gatewayclass.yaml
kubectl apply -f gateway-api/gateway.yaml

# 3. Deploy sample app
kubectl apply -f app/deployment.yaml
kubectl apply -f app/service.yaml

# 4. Create HTTPRoute
kubectl apply -f gateway-api/httproute.yaml

```

Test Access
```
kubectl get svc istio-ingressgateway -n istio-system

curl -H "Host: example.com" http://<EXTERNAL-IP>/
```