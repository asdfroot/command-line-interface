-   rancher log
    ```sh
    kubectl logs --all-containers --since=1h -l app.kubernetes.io/instance=namaservice -n namaNS | grep '"status_code":500"'

    ```

-   rancher rubah duplicate
    ```sh
    kubectl scale deploy namaservice -n namaNS --replicas=5(jumlah 5)
    ```

-   restart service cli
    ```sh
    kubectl get pods -n namaNS | grep -i namaservice | awk '{print $1}' | xargs kubectl delete pods -n namaNS

    ```

-   kubernetes pods ke yaml
    ```sh
    kubectl get pod/svc/ingress/dll namaservice -n namaNS -o yaml>bebas.yaml

    ```

-   kubernetes edit yaml 
    ```sh
    kubectl edit deploy/svc/ingress/dll namaservice -n namaNS

    ```    

-   delete all pods selain running
    ```sh
    kubectl get pods -n NameSpace | grep -v Running | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep -i evicted | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep -i containercreating | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep -i Terminating | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep -i CrashLoopBackOff | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep rb-token | grep -i Error | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```

-   misal restart service NamaPod
    ```sh
    kubectl get pods -n NameSpace | grep -i NamaPod | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep -i NamaPod | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```

-   hapus satu persatu pods:
    ```sh
    kubectl get pods -n NameSpace | grep -v Running | grep NamaPod | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```
    ```sh
    kubectl get pods -n NameSpace | grep -v Running | grep user | awk '{print $1}' | xargs kubectl delete pods -n NameSpace
    ```

-   force delete pod
    ```sh
    kubectl delete pod NamaPod --grace-period-0 --force -n NameSpace
    ```

-   rollback lewat helm
    ```sh
    helm rollback [RELEASE_NAME] -n NameSpace [NUMBER_REVISON]
    ```
    
-   cari log menggunakan stern
    ```sh
    stern -n NameSpace NamaPod --color always | grep 'status_code":5'
    ```
