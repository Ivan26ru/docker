run:
	docker run -p 5050:5050 -d --rm --name reactcontainer ireact
run-dev:
	docker run -p 5050:5050 -d --rm --name reactcontainer  -v /app/node_modules -v "/Users/ivanpisarenko/www/docker/node:/app" ireact
run-dev2: # ссылка pwd работает только, если напрямую вставить в консоль
	docker run -p 5050:5050 -d --rm --name reactcontainer  -v /app/node_modules -v $(pwd):/app ireact
stop:
	docker stop reactcontainer
ps:
	docker ps
psa:
	docker ps -a
build:
	docker build . -t imagereact
images:
	docker images
