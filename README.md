[简体中文](https://github.com/thep0y/up2b/blob/main/README.zh_CN.md)

[Telegram](https://t.me/py_up2b)

# UP2B

A package that can upload pictures to the image bed in `Typora`.

It supports **windows**, **linux** and **macOS** system. 

![Peek 2021-02-13 13-10](https://cdn.jsdelivr.net/gh/thep0y/image-bed/md/1613401533109.png)

# Features

Support the automatic upload of pictures of the following image bed:

- sm.ms
- imgtu.com
- gitee.com
- github.com

Support automatic compression of `jpeg/jpg` and `png` format images.

# How to use

>  **`Typora` must be installed!**

Install the package:

```shell
pip install up2b
```

Usage Options:

```
usage: up2b [-h] [-v] [-aac]
            [-c {0: 'sm.ms', 1: 'imgtu.com', 2: 'gitee.com', 3: 'github.com'} | -l USERNAME PASSWORD | -lg ACCESS_TOKEN USERNAME REPO FOLDER | -p IMAGE_PATH | -ps IMAGE_PATH [IMAGE_PATH ...]]

A package that can upload pictures to the image bed in Typora.

optional arguments:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit
  -aac                  allow automatic image compression
  -c {0: 'sm.ms', 1: 'imgtu.com', 2: 'gitee.com', 3: 'github.com'}, --choose-site {0: 'sm.ms', 1: 'imgtu.com', 2: 'gitee.com', 3: 'github.com'}
                        choose the image bed you want to use and exit
  -l USERNAME PASSWORD, --login USERNAME PASSWORD
                        save the user authentication token after successful login. You
                        must enter the username and password after `-l` or `--login`
  -lg ACCESS_TOKEN USERNAME REPO FOLDER, --login-git ACCESS_TOKEN USERNAME REPO FOLDER
                        save the authentication information of the git website, such as
                        gitee, github
  -p IMAGE_PATH, --image-path IMAGE_PATH
                        upload only one picture
  -ps IMAGE_PATH [IMAGE_PATH ...], --images-path IMAGE_PATH [IMAGE_PATH ...]
                        upload multiple pictures, the maximum is 10 pictures, use spaces
                        to separate each image path.
```
####  1 Choose image bed

When using for the first time, you must first select a image bed. The available image bed list is after the `-c` parameter of **Options**:

- 0
  - sm.ms
- 1
  - imgtu.com
- 2
  - gitee.com
- 3
  - github.com

```shell
# if you want to choose github:
up2b -c 3
```
#### 2 Save authentication information

**General image bed:**

The general picture bed refers to the website that only provides the function of saving images, so **git site** is not included.

When using the general image bed, use `-l` or `--login` to configure authentication information:

```shell
up2b -l username password
```
**Git site:**

Including gitee and github.

When using a git site, use `-lg` or `--login-git` to configure authentication information.

The authentication information includes the following four key parameters:

- `ACCESS_TOKEN`
- `USERNAME` 
- `REPO` 
- `FOLDER`
  - If the folder does not exist, it will be created automatically

For example, I want to save the image in the `md` folder in the `image-bed` repository, and enter this command:

```shell
up2b -lg access_token username image-bed md
```

#### 3 Write the command in typora

Then fill in the command as shown in the figure below.

There is a parameter `-aac` in the command as an optional parameter, which is used to enable the automatic compression function. 

If this parameter is not added, the image will not be automatically compressed when uploading. If the image size exceeds the limit of the image bed, an exception will be thrown during upload.

Adding this parameter will automatically compress images that exceed the limit size to the limit image size or below, ensuring that images can be uploaded smoothly. 

Turn on automatic compression:

```shell
up2b -aac -ps
```

Turn off automatic compression:

```shell
up2b -ps
```

Configure in `Typora` on **windows / linux**:

![截屏2021-04-03 11.04.21](https://cdn.jsdelivr.net/gh/thep0y/image-bed/md/1617419183417.png)

If you want to use it in the **macOS** system, you need to find the absolute path of the up2b command:

![截屏2021-04-03 11.04.48](https://cdn.jsdelivr.net/gh/thep0y/image-bed/md/1617419270287.png)

# End

Now, when you add a picture to `Typora`, it will be automatically uploaded to the picture bed.
