# kustomize-template

## Patch service with alloacted
```
CURRENT_SELECTOR=$(kubectl get svc supertux-fleet-service -o yaml | grep agones.dev/gameserver: | awk '{print $2}')
```
```
ALLOCATED_POD=$(kubectl get gs | grep Allocated | awk '{print $1}')
```
```
kubectl get svc supertux-fleet-service -o yaml | sed -e "${CURRENT_SELECTOR}/${ALLOCATED_POD}/g" | kubectl apply -f -
```