export AOC_BUILD_DIR=$(shell pwd)/collector_build
export SDK=$(shell pwd)/otel_sdk

build-OTelLayer:
	mkdir -p $(ARTIFACTS_DIR)/python
	python3 -m pip install -r $(SDK)/requirements.txt -t $(ARTIFACTS_DIR)/python
	python3 -m pip install -r $(SDK)/requirements-nodeps.txt -t $(ARTIFACTS_DIR)/tmp --no-deps
	python3 -m pip freeze --path $(ARTIFACTS_DIR)/python
	cp -r $(ARTIFACTS_DIR)/tmp/* $(ARTIFACTS_DIR)/python/
	rm -rf $(ARTIFACTS_DIR)/tmp
	cp -r $(SDK)/* $(ARTIFACTS_DIR)/python
	chmod 755 $(ARTIFACTS_DIR)/python/otel-instrument
	rm -rf $(ARTIFACTS_DIR)/python/boto*
	rm -rf $(ARTIFACTS_DIR)/python/urllib3*

	cp -r $(AOC_BUILD_DIR)/* $(ARTIFACTS_DIR)/
