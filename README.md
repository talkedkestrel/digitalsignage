[![Build Status](https://dev.azure.com/fundychan/vsignage/_apis/build/status/vsignage?branchName=master)](https://dev.azure.com/fundychan/vsignage/_build/latest?definitionId=5?branchName=master)
digitalsignage
==============

## Usage

1. Download latest binary for your platform from [GitHub releases](https://github.com/visionect/digitalsignage/releases)
2. Run it from Terminal or Command Prompt

    Optionally you can run it with `-h` flag to see what can be configured.

3. Set Application URL for device in Visionect Server to `http://<server_address>:<server_port>/screen` (default port is 4000)

4. You can use `http://<server_address>:<server_port>/screen?x=<offset_x>&y=<offset_y>` to display only a part of the screen. This enables you to tile multiple displays together and designate one to display a certain part of the image. The parameters disable the automatic image scaling. 


## Development

### Backend

The whole backend is written in `digitalsignage.go`. It contains RESTful(ish) API for uploading, removing and selecting images. It also contains a template view that will display the current image.

We use [bindata](https://github.com/jteeuwen/go-bindata) to package static files in the binary.
For faster development you should use `make debug` that will only link files and not embed them in the binary (so you don't need to recompile every time you change files in `static` folder).


### Frontend

Front end is done with [Polymer](https://www.polymer-project.org/).
Everything custom is in files `static/index.html` and `static/elements/visionect-images.html`.

The page that is used for displaying the content is done in `static/screen.html`.


## Making a release

`make -j4 release` will generate 3 binaries with in `release` folder for linux, OS X and Windows.

If you have `upx` installed you can use `make -j4 compress` which will make much smaller binaries.
