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

## Three-way (merge patches update)

Helm tracks the status of the chart using what is called 'Three-Way (merge patches update)'. This allows Helm to keep track of the status of the chart/app even if it has been updated using another tool than Helm. 

Helm does this by comparing the three manifests, the old chart, the new chart and live-state. Helm then creates a patch that merges the state. 

In a scenario where a Kubernetes resource is updated using a tool other than Helm, Helm will compare the three states and keep both the changes that was made in Helm and the change that was made using the other tool, as long as they don't conflict with eachother.

## Namespaces

By default Helm installs Kubernetes resources inside the default namespace, if specified it can install resources in a specific namespace. The history secrets are stored in the namespace that is specified using the Helm install command.