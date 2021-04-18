IMAGE       = cherokee
REPO        = managedkaos
COMMIT_HASH = $(shell git rev-parse --short HEAD)
TAGS        = alpine latest $(COMMIT_HASH)

all: build tag push

build:
	docker build --tag "$(IMAGE)" .
tag:
	$(foreach tag, $(TAGS), docker image tag "$(IMAGE)" "$(REPO)/$(IMAGE):$(tag)";)

push:
	docker push --all-tags "$(REPO)/$(IMAGE)"

run:
	docker run --rm --name cherokee -d -p 80:80 -p 443:443 -p 9090:9090 cherokee:latest

.PHONY: all build tag push
