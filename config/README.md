# TAP Deployment Instructions

## External Service Connection

Docs - https://docs.vmware.com/en/VMware-Tanzu-Application-Platform/1.8/tap/services-toolkit-tutorials-direct-secret-references.html

### Quick Steps 
Update `external-mysql-db-binding-compatible.yaml` file to include external service details like host, username and password.

1. `kubectl apply -f external-mysql-db-binding-compatible.yaml`
2. `kubectl apply -f stk-secret-reader.yaml`
3. ```
    tanzu service resource-claim create external-mysql-db-claim \
    --resource-name external-mysql-db-binding-compatible \
    --resource-kind Secret \
    --resource-api-version v1
    ```
4. `tanzu service resource-claim list -o wide` Copy value of CLAIM REF
5. Update `workload.yaml` line 13-15 with relevant values. 
