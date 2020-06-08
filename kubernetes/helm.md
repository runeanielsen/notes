# Helm

Helm is a package manager for Kubernetes In Helm packages are called 'Charts'.

If you want to install mysql database with helm the following command is used.

```sh
helm install mysql stable/mysql
```

To upgrade mysql.

```sh
helm upgrade mysql stable/mysql
```

 Instead of using *kubectl* command for each Kubernetes object (yaml file), we instead embed each Kubernetes object in a definition into a single package called a chart.
 
That chart is then passed to Helm and Helm connect to the Kubernetes API. Helm uses the REST Kubernetes API and security layer, like any other Kubernetes client would do. 

The output of the Helm chart installment/upgrade is a release. Helm stores the release history inside Kubernetes as secrets. It centralizes the history of the releases and is stored in the same namespace as the application. The benefit of storing the release information in the Kubernetes cluster, is that everyone else has access to the release information.


