## Load Genarator 
The following parameters are customizable in the load genarator (locust)
  ```sh
        - name: FRONTEND_ADDR
          value: "frontend:80"
        - name: USERS
          value: "10"
        - name: RATE
          value: "1"
    ```
If you need additional test scenarios, please modify the src >> loadgenrator >> locustfile.py 
Additionally, release and upload in docker or private ECR 
and modify the image for loadgenarator in release>kubernetes-manifests.yaml

Please follow release instructions here if you need to release the code too : https://github.com/GoogleCloudPlatform/microservices-demo/blob/main/docs/releasing/README.md 



