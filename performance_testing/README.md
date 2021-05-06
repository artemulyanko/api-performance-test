#Run build
`test docker-compose build`

#Run app
Dev env:
`docker-compose up -d`

Prod env:
`docker-compose -f docker-compose.yml -f docker-compose.override.yml -f docker-compose.prod.yml up -d`

#Run migrations
```
docker-compose exec php bin/console d:m:m
```

# Performance tests
1. *Run from current folder $(pwd)*

2. *Init 30 records with this command:* `ab -p post.txt -T application/json  -n 30 -c 1 https://localhost/notes`

3. *Check records here:* `https://localhost/admin#/notes`

##Testing GET requests:
```
ab -m GET -H "Content-Type: application/json" -n 100 -c 1 https://localhost/notes
ab -m GET -H "Content-Type: application/json" -n 1000 -c 10 https://localhost/notes
ab -m GET -H "Content-Type: application/json" -n 1000 -c 100 https://localhost/notes
ab -m GET -H "Content-Type: application/json" -n 1000 -c 200 https://localhost/notes
```

##Testing POST requests:
```
ab -p post.txt -T application/json  -n 100 -c 1 https://localhost/notes
ab -p post.txt -T application/json  -n 1000 -c 10 https://localhost/notes
ab -p post.txt -T application/json  -n 1000 -c 100 https://localhost/notes
ab -p post.txt -T application/json  -n 1000 -c 200 https://localhost/notes
```
