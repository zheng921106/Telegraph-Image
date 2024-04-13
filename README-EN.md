#  Major additions

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E4%B8%BB%E8%A6%81%E5%A2%9E%E5%8A%A0%E7%9A%84%E5%8A%9F%E8%83%BD)

This branch adds restrictions on image references on the basis of the original version to avoid any person who knows the service address can use it after deployment and avoid the risk of being uploaded "sensitive" content.

Deployment in cloudflare is very simple, after deployment you just need to add a variable to write the domains that are allowed to be accessed in a comma spaced manner. (There are specific steps in the back, deleting the content of the image sensitivity checking service and adding part of the graphical explanation)

  English|[中文](README.md)

# Telegraph-Image

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#telegraph-image)

Free image hosting solution, Flickr/imgur alternative. Uses Cloudflare Pages and Telegraph.

##  characterization

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E7%89%B9%E6%80%A7)

 1. Unlimited number of pictures storage, you can upload unlimited number of pictures

2. No need to buy a server, hosted on Cloudflare's network, completely free when the usage does not exceed Cloudflare's free quota

3. No need to buy a domain name, you can use the `*.pages.dev` free second-level domain name provided by Cloudflare Pages, and also supports binding custom domain names.

4. Support picture review API, you can turn on as needed, after turning on the bad pictures will be automatically blocked, no longer loaded!

5. Support background image management, you can preview the uploaded images online, add white list, black list and other operations

#### 6. Support domain name judgment for image references to avoid image abuse. (Added April 12, 2024)

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#6%E6%94%AF%E6%8C%81%E5%9B%BE%E7%89%87%E5%BC%95%E7%94%A8%E7%9A%84%E5%9F%9F%E5%90%8D%E5%88%A4%E6%96%AD%E9%81%BF%E5%85%8D%E5%9B%BE%E7%89%87%E6%BB%A5%E7%94%A82024%E5%B9%B44%E6%9C%8812%E6%97%A5%E5%A2%9E%E5%8A%A0)

###  limitation

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E9%99%90%E5%88%B6)

1. Since the image files are actually stored in Telegraph, Telegraph limits the size of uploaded images to a maximum of 5MB.

2. Due to the use of Cloudflare's network, the loading speed of images may not be guaranteed in some areas.

3. Cloudflare Function free version of the daily limit of 100,000 requests (i.e., uploading or loading images can not exceed the total number of 100,000 times), such as more than may need to choose to buy Cloudflare Function paid package, such as the opening of the image management function there will be a limit on the number of KV operations, such as more than the need to buy paid! If you exceed the limit, you need to purchase the paid package.

###  Binding of customized domain names

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E7%BB%91%E5%AE%9A%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9F%9F%E5%90%8D)

In the pages custom domain, bind the domain name that exists in cloudflare to the domain name hosted in cloudflare, and the dns records will be modified automatically.[![2](https://camo.githubusercontent.com/14bd9297fd0f53ae224799a97daecce7a6623c9bcf815c8d9548d5812d321e6a/68747470733a2f2f74656c6567726170682d696d6167652e70616765732e6465762f66696c652f3239353436653361373436356130313238316565322e706e67)](https://camo.githubusercontent.com/14bd9297fd0f53ae224799a97daecce7a6623c9bcf815c8d9548d5812d321e6a/68747470733a2f2f74656c6567726170682d696d6167652e70616765732e6465762f66696c652f3239353436653361373436356130313238316565322e706e67)

##  How to deploy

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E5%A6%82%E4%BD%95%E9%83%A8%E7%BD%B2)

###  advance preparation

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E6%8F%90%E5%89%8D%E5%87%86%E5%A4%87)

The only thing you need to prepare ahead of time is a Cloudflare account.

###  hands-on tutorial

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E6%89%8B%E6%8A%8A%E6%89%8B%E6%95%99%E7%A8%8B)

 Deploy the project in 3 easy steps and have your own graphic bed!

1. Fork this repository: Log in to your GitHub account, open this project in your browser, click the Fork button in the navigation bar, and pull it down to your GitHub.

2. Open the Cloudflare Dashboard, go to the Pages management page, select Create Project, and select `连接到 Git 提供程序` . [![1](https://camo.githubusercontent.com/67f04d6cc866bdaf718866c29ccff59afd2b742c37bcd9bd8d90f2cf5d6fbfa1/68747470733a2f2f74656c6567726170682d696d6167652e70616765732e6465762f66696c652f3864346566396237373631613235383231643963322e706e67)](https://camo.githubusercontent.com/67f04d6cc866bdaf718866c29ccff59afd2b742c37bcd9bd8d90f2cf5d6fbfa1/68747470733a2f2f74656c6567726170682d696d6167652e70616765732e6465762f66696c652f3864346566396237373631613235383231643963322e706e67)

3. Follow the instructions on the page to enter the project name, select the git repository you want to connect to, and click `部署站点` to complete the deployment.
    
4.  Configuring Image Management
    

(1) support for image management features, the default is closed, if you need to open, please go to the background after the deployment is complete click `设置` -> `函数` -> `KV 命名空间绑定` -> `编辑绑定` -> `变量名称` Fill out the following: `img_url` `KV 命名空间` Select the KV storage space that you have created well in advance, and then open it. Visit http(s)://your domain name/admin to open the backend management page.

|变量名称|KV 命名空间|
|---|---|
|img_url|Select a pre-created KV storage space|

[![](https://camo.githubusercontent.com/fc772e54ae519d846f80baa9cb6894866815984e9b28ac170eb5cf12c7716274/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f6130633231326435646662363166333635326430372e706e67)](https://camo.githubusercontent.com/fc772e54ae519d846f80baa9cb6894866815984e9b28ac170eb5cf12c7716274/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f6130633231326435646662363166333635326430372e706e67) [![](https://camo.githubusercontent.com/2ccb03fba40676ce418b0574365749928a5878ab6d529f065cde9fbc17064e42/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f3438623933313665643031386232636236376366342e706e67)](https://camo.githubusercontent.com/2ccb03fba40676ce418b0574365749928a5878ab6d529f065cde9fbc17064e42/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f3438623933313665643031386232636236376366342e706e67)

2) New login authentication function is added to the background management page, which is also disabled by default, if you want to enable it, please go to the background after the deployment is completed and click `设置` -> `环境变量` -> `为生产环境定义变量` -> `编辑变量` to add the variables shown in the table below to enable login authentication.

|变量名称|值|
|---|---|
|BASIC_USER =|(Backend administration page login user name)|
|BASIC_PASS =|(Backend administration page login user password)|

[![](https://camo.githubusercontent.com/be7479f98c880f07a30be3eff3c8a3f5a3d9766d367bc41fbf809d2437c2efe1/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f6466663337363439386163383763646237383037312e706e67)](https://camo.githubusercontent.com/be7479f98c880f07a30be3eff3c8a3f5a3d9766d367bc41fbf809d2437c2efe1/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f6466663337363439386163383763646237383037312e706e67)

 3) Add a restriction on the domain name of the website from which the image is obtained:

|变量名称|值|
|---|---|
|DOMAIN_LIST =|(list of domain names separated by English commas)|

The domain name needs to be fully logged in, and if both your website xxx.com and sub.xxx.com are accessible, both xxx.com and sub.xxx.com need to be maintained in a comma-separated list of domain names.

 4) Re-issue the project after parameter maintenance

##  Some limitations:

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E4%B8%80%E4%BA%9B%E9%99%90%E5%88%B6)

Cloudflare KV only has 1000 free writes per day, every new image loaded will take up this write quota, if this quota is exceeded, the image management backend will not be able to record the newly loaded image.

Up to 100,000 free reads per day, with each image load taking up the quota (in the absence of caching, if your domain has caching enabled in Cloudflare, the quota is taken up when the cache misses), beyond which features such as black and white lists may be disabled

Maximum 1,000 free deletions per day, each image record will take up the quota, beyond which no image records can be deleted.

Maximum 1,000 free listing operations per day, every time you open or refresh the backend/admin will take up the quota, more than that will be carried out in the background image management

In the vast majority of cases, the free quota is basically enough, and can be a little more than a little, not have exceeded the immediate deactivation, and each quota is calculated separately, a certain operation exceeds the free quota will only be deactivated after the operation, does not affect the other functions, that is, even if my free writing quota is exhausted, my read and write functions are not affected, the picture can be loaded normally, just can not be in the background of the picture management to see the new I just can't see the new images in the image management background.

If you don't have enough free credits, you can purchase a paid version of Cloudflare Workers from Cloudflare yourself, starting at $5 per month, with a per-volume fee and none of the aforementioned credit limitations.

[![](https://camo.githubusercontent.com/f6880733413c469c4bac22a46ec37eae191a351d6b47e3f87c0360cf77e0e126/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f6235313434363761346233626530353637613736662e706e67)](https://camo.githubusercontent.com/f6880733413c469c4bac22a46ec37eae191a351d6b47e3f87c0360cf77e0e126/68747470733a2f2f696d2e6775726c2e65752e6f72672f66696c652f6235313434363761346233626530353637613736662e706e67)In addition, changes made to environment variables will take effect the next time they are deployed, so remember to redeploy it if you change environment variables to enable or disable features.

###  (express) thanks

[](https://github.com/xiaodao2026/Telegraph-Image/blob/main/README.md#%E6%84%9F%E8%B0%A2)

@cf-pages offers the Telegraph-Image feature to help me with image storage when my vps is low on space.
