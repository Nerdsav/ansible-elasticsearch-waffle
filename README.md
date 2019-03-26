
## General

A small example how to use Ansible to install predefined templates into an Elasticsearch cluster.


## Index Template

You can install index templates manually with the REST API.

For instance create a template named `jobads` and pass default values.

```json
PUT _template/jobads
{"order":1,"version":1,"index_patterns":["jobads-*"],"settings":{"number_of_shards":1,"number_of_replicas":0}}
``` 

## Install with Ansible

If you install Elasticsearch with Ansible you can also apply the index template after the deployment. This is useful if
you have an ephemeral installation of Elasticsearch.

To run the playbook

```bash
ansible-playbook install-templates.yml
```

The playbook steps are

- check if Elasticsearch is responding on cluster health query
- check if template exists
- install template

