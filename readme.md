# xldflags

Simple package to be the target of values set at compile time
using ldflags. Other packages can import xldflags to access the set
variables, making them 'globally' accessible.

package xldflags exports the following variables:

	VERSION		string e.g. "1.0.40"
	APP_NAME	string e.g. "Long product name"
	PRODUCT		string e.g. "short-name"

To set these variables when compiling using a BASH Script so as:

	#!/bin/bash
	VERSION="1.0.40"
	PRODUCT="short-name"
	APP_NAME="Long product name"
	PKG="solutionbase.co.uk/xldflags"
	go build -o $PRODUCT -ldflags "-X $PKG.VERSION=$VERSION -X $PKG.PRODUCT=$PRODUCT -X $PKG.APP_NAME=$APP_NAME" *.go
