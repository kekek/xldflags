# xldflags

Simple package to be the target of values set at compile time using ldflags. Other packages can import xldflags to access the values, making them 'globally' accessible.

Package xldflags exports the following variables:

	VERSION		string e.g. "1.0.40"
	APP_NAME	string e.g. "Long product name"
	PRODUCT		string e.g. "short-name"

To set these variables when compiling use a BASH Script so as:

	#!/bin/bash
	VERSION="1.0.40"
	PRODUCT="short-name"
	APP_NAME="Long product name"
	PKG="github.com/kgolding/xldflags"
	go build -o $PRODUCT -ldflags "-X '$PKG.VERSION=$VERSION' -X '$PKG.PRODUCT=$PRODUCT' -X '$PKG.APP_NAME=$APP_NAME'" *.go

In your go packages, you can access the fields like so:

	package main
	import (
		"fmt"
		"github.com/kgolding/xldflags"
	)
	func main() {
		fmt.Println("Version: ", xldflags.VERSION)
	}
