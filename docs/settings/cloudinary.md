# Cloudinary as media management

**Uvendia** is using **[Cloudinary](https://cloudinary.com)** for uploading and manipulation of media items like images, videos and files. With **Cloudinary** you get your first 25 GB of storage for free. Please take a look at their website under the tab _Pricing_ to see everything they have to offer. 

## CDN
**Cloudinary** is also a great CDN (Content Delivery Network). Your media items are being stored on geographically dispersed servers for fast delivery.

## Configuring Cloudinary
After creating your account on [Cloudinary](https://cloudinary.com/users/register/free) you can configure the settings here below in your web.config:

```xml
<add key="Cloudinary.Name" value="[CLOUD NAME]" />
<add key="Cloudinary.API.Key" value="[API KEY]" />
<add key="Cloudinary.API.Secret" value="[API SECRET]" />
<add key="Cloudinary.Url" value=" https://res.cloudinary.com/" />
```