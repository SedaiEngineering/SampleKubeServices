# SampleKubeServices
## Quickstart (GKE)

1. Ensure you have the following requirements:
   - Shell environment with  `git`, and `kubectl`.
    

2. Install istio using any of  the steps here : https://istio.io/latest/docs/setup/install/
3. Create a new namespace
4. Add the Istio injection labels to the new namespace.

   ```sh
   kubectl label namespace <new-namespace> \
     istio.io/rev- istio-injection=enabled --overwrite
   ```
5.  Clone the latest major version.

   ```sh
   git clone --depth 1 --branch v0 https://github.com/SedaiEngineering/SampleKubeServices.git
   cd microservices-demo/
   ```

   The `--depth 1` argument skips downloading git history.


6. Deploy Online Boutique to the cluster.

   ```sh
   kubectl apply -f ./release/kubernetes-manifests.yaml
   ```

7. Wait for the pods to be ready.

   ```sh
   kubectl get pods
   ```

   After a few minutes, you should see the Pods in a `Running` state:

   ```
   NAME                                     READY   STATUS    RESTARTS   AGE
   adservice-76bdd69666-ckc5j               1/1     Running   0          2m58s
   cartservice-66d497c6b7-dp5jr             1/1     Running   0          2m59s
   checkoutservice-666c784bd6-4jd22         1/1     Running   0          3m1s
   currencyservice-5d5d496984-4jmd7         1/1     Running   0          2m59s
   emailservice-667457d9d6-75jcq            1/1     Running   0          3m2s
   frontend-6b8d69b9fb-wjqdg                1/1     Running   0          3m1s
   loadgenerator-665b5cd444-gwqdq           1/1     Running   0          3m
   paymentservice-68596d6dd6-bf6bv          1/1     Running   0          3m
   productcatalogservice-557d474574-888kr   1/1     Running   0          3m
   recommendationservice-69c56b74d4-7z8r5   1/1     Running   0          3m1s
   redis-cart-5f59546cdd-5jnqf              1/1     Running   0          2m58s
   shippingservice-6ccc89f8fd-v686r         1/1     Running   0          2m58s
   ```

7. Access the web frontend in a browser using the frontend's external IP.

   ```sh
   kubectl get service frontend-external | awk '{print $4}'
   ```


   Visit `http://EXTERNAL_IP` in a web browser to access your instance of Online Boutique.

8.
9. Congrats! You've deployed the default Online Boutique with monitoring
