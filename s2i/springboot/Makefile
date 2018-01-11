IMAGE_NAME = springboot
TAG = 1.1
.PHONY: build
build:
	docker build -t $(IMAGE_NAME):$(TAG) .

.PHONY: test
test:
	docker build -t $(IMAGE_NAME)-candidate .
	IMAGE_NAME=$(IMAGE_NAME)-candidate test/run
