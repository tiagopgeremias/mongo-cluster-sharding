# mongo-cluster-sharding

Provisioning a cluster MongoDB with Sharding and ReplicaSet

## Dependencies

- community.mongodb.mongodb_shard – Add or remove shards from a MongoDB Cluster: https://docs.ansible.com/ansible/latest/collections/community/mongodb/mongodb_shard_module.html

```sh
ansible-galaxy collection install community.mongodb
```

## Keyfile

Você pode gerar um arquivo-chave usando qualquer método de sua escolha. Por exemplo, a operação a seguir usa opensslpara gerar uma cadeia de caracteres pseudoaleatória complexa de 1024 para usar como uma senha compartilhada. Em seguida, ele usa chmodpara alterar as permissões do arquivo para fornecer permissões de leitura apenas para o proprietário do arquivo:

```sh
openssl rand -base64 756 > <path-to-keyfile>
```

Se você estiver adicionando um novo nó de ReplicaSet em um cluster existente, você deve utilizar a mesma chave que ja consta nos ReplicaSet provisionados.
Localização da chave em nós ja provisonados:

```sh
/data/mongo_security.key
```

## Executando o playbook

```sh
ansible-playbook -i inventory/hosts play.yml -e security_key=<path-to-keyfile> -e user_admin=<admin-user> -e pass_admin=<admin-pass>
```