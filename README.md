# install
```sh
apt update

apt upgrade

curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -

echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list

apt update

apt install elasticsearch
```

# configure
```sh
nano /etc/elasticsearch/elasticsearch.yml

systemctl start elasticsearch

systemctl enable elasticsearch
```

# secure
```sh
ufw allow from 198.51.100.0 to any port 9200

ufw enable

ufw status
```

# test
```sh
curl -X GET 'http://localhost:9200'

curl -XGET 'http://localhost:9200/_nodes?pretty'
```

# use
```sh
curl -XPOST -H "Content-Type: application/json" 'http://localhost:9200/tutorial/helloworld/1' -d '{ "message": "Hello World!" }'

curl -X GET -H "Content-Type: application/json" 'http://localhost:9200/tutorial/helloworld/1' -d '{ "message": "Hello World!" }'

curl -X PUT -H "Content-Type: application/json"  'localhost:9200/tutorial/helloworld/1?pretty' -d '
{
  "message": "Hello, People!"
}'

curl -X GET -H "Content-Type: application/json" 'http://localhost:9200/tutorial/helloworld/1?pretty'
```

# docs
https://www.elastic.co/guide/index.html

https://stackoverflow.com/questions/42127894/whats-the-difference-between-search-as-you-type-and-context-suggester

https://spinscale.de/posts/2020-05-29-implementing-a-linkedin-like-search-as-you-type-with-elasticsearch.html

https://coralogix.com/blog/elasticsearch-autocomplete-with-search-as-you-type/
