include env_make
NS = sandeeps
VERSION = latest
REPO = docker-ci
NAME = docker-ci
INSTANCE = default

.PHONY: build push start stop shell run rm release 

build:
	docker build -t ${NS}/${REPO}:${VERSION} .

push:
	docker push ${NS}/${REPO}:${VERSION}

start:
	docker run -d --name ${NAME}-${INSTANCE} ${PORTS} ${VOLUMES} ${ENV} ${NS}/${REPO}:${VERSION}
	
stop:
	docker stop ${NAME}-${INSTANCE}
	
shell:
	docker run --rm  --name ${NAME}-${INSTANCE} -i -t ${PORTS} ${VOLUMES} ${ENV} ${NS}/${REPO}:${VERSION} /bin/bash
	
run:
	docker run --rm  --name ${NAME}-${INSTANCE} ${PORTS} ${VOLUMES} ${ENV} ${NS}/${REPO}:${VERSION}
 
rm:
	docker rm ${NAME}-${INSTANCE}

release:build
	make push -e VERSION=${VERSION}
	
default: build