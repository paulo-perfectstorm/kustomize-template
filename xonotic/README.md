## Patch service with allocated
```
CURRENT_SELECTOR=$(kubectl get svc xonotic-fleet-service -o yaml | grep gameserver: | awk '{print $2}')
```
```
ALLOCATED_POD=$(kubectl get gs | grep Allocated | awk '{print $1}')
```
```
kubectl get svc xonotic-fleet-service -o yaml | sed -e "s/gameserver: ${CURRENT_SELECTOR}/gameserver: ${ALLOCATED_POD}/g" | kubectl apply -f -
```