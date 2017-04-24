# Getting image files from your Google.Drive to a Jetstream VM

In the US, academic institutions increasingly have set up user email accounts through Google.
Some of these accounts have unlimited Google.drive storage as a service for faculty and students.

One of the issues with uploading or downloading a large number of images to a Google.Drive 
account through a GUI (i.e. Google's Chrome Web Browser) is the limit to the number of files, 
the speed of the uploads, and the size of the downloads. Typically a download directly from a 
Google.Drive account through Chrome is limited to <2Gb and is zipped by Google before starting.

While the browser can work well for uploading a large number sUAS imagery - both from the field and from PC,
downloading a large quantity of images as .zip files from the Google.drive can be tiresome and difficult.

To get around thes problems we can use 3rd party applications like `drive` a command line client 
written in Google's `go` language.

## Install Go language

Google.Drive uses the `go` language. In order to work with it you need to [install `go`](https://golang.org/doc/install) onto the VM.

```
$ wget https://storage.googleapis.com/golang/go1.8.1.linux-amd64.tar.gz
```

```
$ tar -C /usr/local -xzf go1.8.1.linux-amd64.tar.gz
```

In `/etc/profile` add: `export PATH=$PATH:/usr/local/go/bin`

In `~/.bashrc` add:  
```
export GOPATH=$HOME/go
export PATH=$GOPATH:$GOPATH/bin:$PATH
```
Follow the `go`instructions to [test the installation](https://golang.org/doc/install#testing)

## Install `drive` a Google Drive Client for commandline

[`drive`](https://github.com/odeke-em/drive#installing) is a command line client using Go language

Add the GOPATH to `.bashrc`

```
cat << ! >> ~/.bashrc
  export GOPATH=\$HOME/gopath
  export PATH=\$GOPATH:\$GOPATH/bin:\$PATH
  !
source ~/.bashrc # To reload the settings and get the newly set ones # Or open a fresh terminal
```

Install `drive` using `go`

```
go get -u github.com/odeke-em/drive/cmd/drive
```

### Initialize `drive` with your Google account

```
mkdir ~/gdrive
drive init ~/gdrive
```

Follow the instructions for copying and pasting the html for authentication

Test your installation

```
drive ls
```
# Pull data from your Google.drive account onto the VM

```
drive pull your/google/drive/folders/here
```
