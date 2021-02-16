# etcd 

etcd is a distributed reliable key-value store for the most critical data of a distributed system, with a focus on being:

* *Simple*: well-defined, user-facing API (gRPC)
* *Secure*: automatic TLS with optional client cert authentication
* *Fast*: benchmarked 10,000 writes/sec
* *Reliable*: properly distributed using Raft

etcd is written in Go and uses the [Raft][raft] consensus algorithm to manage a highly-available replicated log.

etcd is used [in production by many companies](./ADOPTERS.md), and the development team stands behind it in critical deployment scenarios, where etcd is frequently teamed with applications such as [Kubernetes][k8s], [locksmith][locksmith], [vulcand][vulcand], [Doorman][doorman], and many others. Reliability is further ensured by [**rigorous testing**](https://github.com/etcd-io/etcd/tree/master/tests/functional).

See [etcdctl][etcdctl] for a simple command line client.

[raft]: https://raft.github.io/
[k8s]: http://kubernetes.io/
[doorman]: https://github.com/youtube/doorman
[locksmith]: https://github.com/coreos/locksmith
[vulcand]: https://github.com/vulcand/vulcand
[etcdctl]: https://github.com/etcd-io/etcd/tree/master/etcdctl

## Getting started
#### file structure
    .
    ├──  repository name            
    │  ├──   versions             #   version of the chart 
    │     ├── flavorname-config.json  #default values  for template flavor values
    │     ├── flavorname-readme.md    #specfic readme file per flavor
    │     ├── flavorname-values.json  #values per flavor
        ├──    metadata.json            #   metadata for the template 
#### metadata.json

```
{
    "repository_name": NAME OF THE REPOSITORY,
    "repository": URL OF THE REPOSITORY,
    "chart_name": NAME OF THE CHART,
    "logo_image": URL OF THE CHART,
    "description": SMALL DESCRIPTION OF THE CHART
}
```
#### flavorname-config.json

```
{
  "default_value_array": [
      {
        "path": YAML OR JSON PATH FOR THE VARIABLE -  | ,
        "value": VALUE FOR THE VARIABLE -  | required,
        "description": SMALL DESCRIPTION FOR DEFAULT VALUE - text | optional,
        "cluster_resources": SPECIAL CLUSTER RESOURCES - string | optional,
        "regex":  array | optional
      }
  ]
}
```

| Key | Description | types | required
| ------ | ------ | ------ | ------ | 
| path | YAML OR JSON PATH FOR THE VARIABLE | string | required
| value | VALUE FOR THE VARIABLE | string,boolean,array,integer | required
| description | SMALL DESCRIPTION FOR DEFAULT VALUE | text | optional
| cluster_resources |  SPECIAL CLUSTER RESOURCES | string | optional
| regex | IF YOU HAVE SPECIAL REGEXS | array | optional


