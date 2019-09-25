# Welcome to Uvendia
## Introduction

**Uvendia** is an e-commerce component that runs on **Umbraco 8**.
[Umbraco](https://umbraco.com/) is an open-source content management system (CMS) platform for publishing content on the World Wide Web and intranets. It is written in C# and deployed on Microsoft based infrastructure. Since version 4.5, the whole system has been available under an MIT License.

> **Uvendia** e-commerce component makes it very easy for the **Umbraco** user to manage their products and/or events (ticket sales) they want to sell on the internet.

## Hierarchy
This is how **Uvendia** is designed:

```text
└── Store 1
    ├── Category 1
            └── Product 1
                ├── Variant 1
                ├── Variant 2
                └── Variant 3
        ├── Subcategory 1
            └── Product 2
                ├── Variant 1
                ├── Variant 2
                └── Variant 3
        └── Subcategory 2
            ├── Product 1             
            └── Product 3    
    ├── Category 2
        ├── Product 2
        ├── Product 3
        ├── Product 4
            ├── Variant 1
            ├── Variant 2
            └── Variant 3
        └── Product 5
    └── Category 3
└── Store 2
    ├── Category 1
            └── Product 1
    ├── Category 2
        ├── Product 2
        └── Product 3
    ├── Category 3
        ├── Product 4
        ├── Product 5
        ├── Product 6
        └── Product 7
    └── Category 4
├── Event 1    
├── Event 2
├── Event 3
└── Event 4    
```
## Store, category and product
As seen in the hierarchy above, it is possible to create multiple stores and each store can have one or more categories and each category can have one or more subcategories. To each category is it possible to assign one ore more products. A product can be assign to multiple categories.

### Product variant
A product can consist of multiple variants. For instance you have a product _tie_. A tie is sold in multiple colors like: _red_, _yellow_ and _green_. Each color can be a ```variant``` of the product _tie_.

## Event
With **Uvendia** e-commerce component is it also possible to create events and sell tickets to your customers. These are the event types:
* Workshop
* Event
* Party
* Meeting
* Networking
* Education
* Eat and/or drinks
* Concert
* Cinema
* Other

> The system will generates the tickets for you when the transaction has been fully processed. Each is rendered with a UNIQUE ```QR-Code``` and ```Bar-code```.

## Image, file and video management
Uvendia is using **[Cloudinary](https://cloudinary.com/)** for uploading and manipulation of media items like images, videos and files. **Cloudinary** is a SaaS technology company that provides a cloud-based image and video management solution + CDN. It enables users to upload, store, manage, manipulate and deliver images, videos and files for websites and apps. The media items items are being stored on geographically dispersed servers for fast delivery.

## Dapper ORM
The ORM (Object Relational Mapper) used is **[Dapper](https://github.com/StackExchange/Dapper)** is a simple object mapper for .NET and own the title of King of Micro ORM in terms of speed and is virtually as fast as using a raw ADO.NET data reader. Dapper is developed by [StackOverflow](https://github.com/StackExchange).

## License
If you are running Umbraco's **Uvendia** plug-in component on your local machine, no license is required. When you are convinced about the product and want to deploy it to your development, staging or production environment, you are going to need a License for that.
> License is only required for the Umbraco's **Uvendia** component. NO License is needed for the actual e-commerce webshop that is using the ```Uvendia.Domain.dll``` assembly.
