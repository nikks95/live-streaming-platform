ROOT_DIR := $(realpath $(dir $(lastword $(MAKEFILE_LIST)))/..)

COMPOSE_FILE := $(ROOT_DIR)/infra/docker-compose.yml

DOCKER_COMPOSE := $(shell command -v docker-compose 2>/dev/null || echo "docker compose")

.PHONY: up down logs

up:
	$(DOCKER_COMPOSE)  -f $(COMPOSE_FILE) up -d

down:
	$(DOCKER_COMPOSE) -f $(COMPOSE_FILE) down

logs:
	$(DOCKER_COMPOSE) -f $(COMPOSE_FILE) logs -f