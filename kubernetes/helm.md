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

## Helm Chart structure

The simplest Helm Chart structure is the following

**chart**
-- Chart.yaml
-- **templates**
    -- my-resource-one.yaml
    -- my-resource-two.yaml
    -- my-resource-three.yaml

### Example of a Chart.yaml file

```yaml
apiVersion: v2
name: my-chart-name
appVersion: "1.0"
description: A Helm chart for my-chart-name 1.0
version: 0.1.0
type: application
```

## Release



### Release revision

When you update a Kubernetes resource inside of a Helm Chart you don't create a new release, but you make a new revision of the release. 

Release revision should not be confused with Chart version. The Charts version refers to a change in the Charts file structure, meaning a change in the application definition. An example could be new Kubernetes resources being added to the Chart.
