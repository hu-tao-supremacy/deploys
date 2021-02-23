ROOT_DIR:=.
SECRETS_DIR:=$(ROOT_DIR)/secrets
SECRETS:=$(wildcard $(SECRETS_DIR)/*-secret.yaml)
SOURCES:=$(patsubst $(SECRETS_DIR)/%-secret.yaml, %-secret, $(SECRETS))

$(SOURCES):
	@python3 ./secret-encode $(SECRETS_DIR)/$@.yaml | kubeseal --format yaml > $@.sealed.yaml

sealed-secrets: $(SOURCES)
