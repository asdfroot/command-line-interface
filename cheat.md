-   rancher log
    ```sh
    kubectl logs --all-containers --since=1h -l app.kubernetes.io/instance=namaservice -n namaNS | grep '"status_code":500"'

    ```

-   rancher rubah duplicate
    ```sh
    kubectl scale deploy namaservice -n namaNS --replicas=5(jumlah 5)
    ```

-   restart service tertentu cli
    ```sh
    kubectl get pods -n namaNS | grep -i namaservice | awk '{print $1}' | xargs kubectl delete pods -n namaNS

    ```

-   restart semua service di namespace cli
    ```sh
    kubectl get pod -n namaNS | awk '{print $1}' | xargs kubectl delete pod -n namaNS

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

-   seteleh ubah jaringan 8.8.8
    ```sh
    echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
    ```
    
-   kubernetes. melihat info konteks / melihat nama cluster saat ini 
    ```sh
    kubectl config get-contexts
    ```    
    
-   kubernetes. pindah konteks / pindah cluster 
    ```sh
    kubectl config use-context NamaCluster
    ```  
    
-   kubernetes. pindah NameSpace / pindah NameSpace tanpa perintah Namespace 
    ```sh
    kubectl config set-context --current --namespace NamaNStujuan
    ```
    
-   izin/permission file/folder akses nginx
    ```sh
    sudo chown www-data:www-data ~/NamaFolder -R
    ```
        
-   kirim file bumi ke pluto | scp
    ```sh
    scp Namafile.3gp NamaUser@ipDomain:/nama/folder/tujuan
    ```  

-   kirim file pluto ke bumi | scp
    ```sh
    scp NamaUser@ipDomain:/nama/folder/Namafile.3gp /home/tujuan/folder
    ```

-   hapus log catalina.out
    ```sh
    cat /dev/null > catalina.out
    ```

-   perbedaan isi teks file
    ```sh
    diff -c namafile1.txt namafile2.txt
    ```      
