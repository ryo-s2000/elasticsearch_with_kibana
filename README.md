```
docker-compose up
```

kibana
```
http://localhost:5601/app/dev_tools#/console
```

```
PUT kuromoji_analyzer
{
  "mappings": {
    "properties": {
      "text":{
        "type": "text",
        "analyzer": "kuromoji"
      }
    }
  }
}

POST _analyze
{
  "analyzer": "kuromoji",
  "text": "東京都に行く"
}

PUT kuromoji_analyzer/_doc/1
{
  "text":"東京都に行く"
}

GET kuromoji_analyzer/_search
{
  "query": {
    "match": {
      "text": "東京"
    }
  }
}
```
