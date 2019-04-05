PROJROOT := $(CURDIR)/../..


.PHONY: all
all: clean build dist

.PHONY: build
build:
	mkdir build
	cd rapidjson; xcodebuild -sdk iphonesimulator -target rapidjson -scheme rapidjson -derivedDataPath ../build
	cd rapidjson; xcodebuild -sdk iphoneos -target rapidjson_sim -scheme rapidjson -derivedDataPath ../build
	lipo -create build/Build/Products/Release-iphoneos/librapidjson.a \
	     -create build/Build/Products/Release-iphonesimulator/librapidjson.a \
	     -output build/librapidjson.a

.PHONY: dist
dist:
	rm -rf $(PROJROOT)/dist/unity/Internal.Any
	mkdir -p $(PROJROOT)/dist/unity/Internal.Any
	cp build/librapidjson.a $(PROJROOT)/dist/unity/Internal.Any

.PHONY: clean
clean:
	rm -rf build
