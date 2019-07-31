```
                   _
   _ __  _   _ ___(_)_ __
  | '_ \| | | |_  / | '_ \
  | |_) | |_| |/ /| | |_) |
  | .__/ \__, /___|_| .__/
  |_|    |___/      |_|
```

# pyzip

Pyzip is a simple bash script that allows you to quickly package a python project in a `.zip` file ready to upload in AWS Lambda.  

![Alt Text](https://github.com/smallwat3r/pyzip/blob/master/demo/demo.gif)

## Set up

Clone this repository and run the following commands.  
```sh
make install
```
OR  
```sh
cp src/pyzip /usr/local/bin/pyzip && chmod 755 /usr/local/bin/pyzip
```

In `~/.pyzipconfig` you can enter Pyzip configurations   
- `build_folder`: name of the folder that will be created to install the dependencies and store the ouput zip file (default `pyzip_build`).  
- `maxdepth`: the max depth of folders in your project. For instance you should avoid running it from root (default `4`)   
- `python`: the python command version of your system (default `python3`).  

## How to

To run, you must have create a virtual env named `venv` in the same folder from where you will run `pyzip`.  
Indeed, Pyzip will source this virtual env to make sure the dependencies it will install are running for the same software versions.  

You can **exclude** files or entire folders from Pyzip using `-e` (stands for exclude).  
**Note that you have to repeat `e` for each files or folders.**  

```sh
pyzip -e readme.md -e logs -e test/dummy.txt
```

If will generate a new folder `pyzip_build` with your `build.zip` file ready to be uploaded in Lambda.  
In `pyzip_build/build` you can also see the detail of the files, plus dependencies installed.  

