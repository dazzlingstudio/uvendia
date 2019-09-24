# Mapping your assets

## Language configuration
Make sure you have configured the necessary [languages](/settings/languages.md) that your webshop will be using before starting importing.

## Extended properties configuration
Make sure you have configured the necessary [Property Definitions](/settings/propertydefinition.md) that your asset will be using before starting importing.

## Price definition configuration
Make sure you have configured the necessary [Price Definitions](/settings/pricedefinition.md) that your asset will be using before starting importing.

## Example code

### Mapping the stores
> Make sure you pass the ``import mode`` on each asset.
Import mode can be: ``Insert``, ``Update`` or ``Delete``

```C#
/// <summary>
/// Creates the store requests.
/// </summary>
/// <param name="mode">The import mode.</param>
/// <returns></returns>
public static IEnumerable<StoreRequest> CreateStoreRequests(ImportMode mode = ImportMode.Insert)
{
    var store1 = new StoreRequest()
    {
        ExternalId = "TESTSTORE1",
        Name = "Test Store 1",
        Published = true,
        ImportMode = mode,
        Translations = new List<TranslationRequest>
        {
            new TranslationRequest
            {
                CultureInfoName = "en-US",
                DisplayName = "TEST EN STORE",
                LongDescription = "TEST EN STORE LongDescription 1",
                ShortDescription = "TEST EN STORE LongDescription 1"
            },
            new TranslationRequest
            {
                CultureInfoName = "nl",
                DisplayName = "TEST NL STORE DisplayName 1",
                LongDescription = "TEST NL STORE LongDescription 1",
                ShortDescription = "TEST NL STORE LongDescription 1"
            }
        },
        PropertyDefinitionName = "def store test",
        Properties = new List<PropertyValueRequest>
        {
            new PropertyValueRequest
            {
                PropertyName = "test 1",
                PropertyValue = "test 1 STORE"
            }
        },
        CreatedBy = "Unit test"
    };

    var store2 = new StoreRequest()
    {
        ExternalId = "TESTSTORE2",
        Name = "Test Store 2",
        Published = true,
        ImportMode = mode,
        Translations = new List<TranslationRequest>
        {
            new TranslationRequest
            {
                CultureInfoName = "en-US",
                DisplayName = "TEST EN STORE DisplayName 2",
                LongDescription = "TEST EN STORE LongDescription 2",
                ShortDescription = "TEST EN STORE LongDescription 2"
            },
            new TranslationRequest
            {
                CultureInfoName = "nl",
                DisplayName = "TEST NL STORE DisplayName 2",
                LongDescription = "TEST NL STORE LongDescription 2",
                ShortDescription = "TEST NL STORE LongDescription 2"
            }

        },
        PropertyDefinitionName = "def store test",
        Properties = new List<PropertyValueRequest>
        {
            new PropertyValueRequest
            {
                PropertyName = "test 1",
                PropertyValue = "test 2 STORE"
            }
        },
        Categories = CreateCategoryRequests(mode),
        CreatedBy = "Unit test"
    };


    return new[] { store1, store2 };
}
```

### Mapping the categories

```C#
/// <summary>
/// Creates the category requests.
/// </summary>
/// <param name="mode">The import mode.</param>
/// <returns></returns>
public static IEnumerable<CategoryRequest> CreateCategoryRequests(ImportMode mode = ImportMode.Insert)
{
    var cat1 = new CategoryRequest()
    {
        ExternalId = "TESTCATEGORY1",
        Name = "Test Category 1",
        Published = true,
        ImportMode = mode,
        Translations = new List<TranslationRequest>
        {
            new TranslationRequest
            {
                CultureInfoName = "en-US",
                DisplayName = "TEST EN CATEGORY DisplayName 1",
                LongDescription = "TEST EN CATEGORY LongDescription 1",
                ShortDescription = "TEST EN CATEGORY LongDescription 1"
            },
            new TranslationRequest
            {
                CultureInfoName = "nl",
                DisplayName = "TEST NL CATEGORY DisplayName 1",
                LongDescription = "TEST NL CATEGORY LongDescription 1",
                ShortDescription = "TEST NL CATEGORY LongDescription 1"
            }

        },
        PropertyDefinitionName = "def category test 2",
        Properties = new List<PropertyValueRequest>
        {
            new PropertyValueRequest
            {
                PropertyName = "test 1",
                PropertyValue = "test 1 CATEGORY"
            },
            new PropertyValueRequest
            {
                PropertyName = "test 2",
                PropertyValue = "test 2 CATEGORY"
            },
            new PropertyValueRequest
            {
                PropertyName = "test 3",
                PropertyValue = "test 3 CATEGORY"
            }
        },
        Store = new StoreRequest { ExternalId = "TESTSTORE2", Name = "Test Store 2" },
        SubCategories = new List<CategoryRequest>
        {
            new CategoryRequest
            {
                ExternalId = "TESTSUBCATEGORY1",
                Name = "Test SUB Category 1",
                Published = true,
                ImportMode = mode,
                Translations = new List<TranslationRequest>
                {
                    new TranslationRequest
                    {
                        CultureInfoName = "en-US",
                        DisplayName = "TEST SUB EN DisplayName 1",
                        LongDescription = "TEST SUB EN LongDescription 1",
                        ShortDescription = "TEST SUB EN LongDescription 1"
                    },
                    new TranslationRequest
                    {
                        CultureInfoName = "nl",
                        DisplayName = "TEST SUB NL DisplayName 1",
                        LongDescription = "TEST SUB NL LongDescription 1",
                        ShortDescription = "TEST SUB NL LongDescription 1"
                    }

                },
                PropertyDefinitionName = "def category test",
                Properties = new List<PropertyValueRequest>
                {
                    new PropertyValueRequest
                    {
                        PropertyName = "test 1",
                        PropertyValue = "test SUB 1"
                    }
                },
                Store = new StoreRequest { ExternalId = "TESTSTORE2", Name = "Test Store 2" },
                SubCategories = new List<CategoryRequest>
                {
                    new CategoryRequest
                    {
                        ExternalId = "TESTSUBSUBCATEGORY1",
                        Name = "Test SUB SUB Category 1",
                        Published = true,
                        ImportMode = mode,
                        Translations = new List<TranslationRequest>
                        {
                            new TranslationRequest
                            {
                                CultureInfoName = "en-US",
                                DisplayName = "TEST SUB SUB EN DisplayName 1",
                                LongDescription = "TEST SUB SUB EN LongDescription 1",
                                ShortDescription = "TEST SUB SUB EN LongDescription 1"
                            },
                            new TranslationRequest
                            {
                                CultureInfoName = "nl",
                                DisplayName = "TEST SUB SUB NL DisplayName 1",
                                LongDescription = "TEST SUB SUB NL LongDescription 1",
                                ShortDescription = "TEST SUB SUB NL LongDescription 1"
                            }

                        },
                        PropertyDefinitionName = "def category test",
                        Properties = new List<PropertyValueRequest>
                        {
                            new PropertyValueRequest
                            {
                                PropertyName = "test 1",
                                PropertyValue = "test SUB 1"
                            }
                        },
                        Store = new StoreRequest { ExternalId = "TESTSTORE2", Name = "Test Store 2" }
                    }
                }
            }
        },
        CreatedBy = "Unit test"
    };    

    var cat2 = new CategoryRequest()
    {
        ExternalId = "TESTCATEGORY2",
        Name = "Test Category 2",
        Published = true,
        ImportMode = mode,
        Translations = new List<TranslationRequest>
        {
            new TranslationRequest
            {
                CultureInfoName = "en-US",
                DisplayName = "TEST EN CATEGORY DisplayName 2",
                LongDescription = "TEST EN CATEGORY LongDescription 2",
                ShortDescription = "TEST EN CATEGORY LongDescription 2"
            },
            new TranslationRequest
            {
                CultureInfoName = "nl",
                DisplayName = "TEST NL CATEGORY DisplayName 2",
                LongDescription = "TEST NL CATEGORY LongDescription 2",
                ShortDescription = "TEST NL CATEGORY LongDescription 2"
            }

        },
        PropertyDefinitionName = "def category test",
        Properties = new List<PropertyValueRequest>
        {
            new PropertyValueRequest
            {
                PropertyName = "test 1",
                PropertyValue = "test 2 CATEGORY"
            }
        },
        Store = new StoreRequest { ExternalId = "TESTSTORE2", Name = "Test Store 2" },
        CreatedBy = "Unit test"
    };

    return new[] { cat1, cat2 };
}
```

### Mapping the categories

```C#
/// <summary>
/// Creates the product requests.
/// </summary>
/// <param name="mode">The mode.</param>
/// <returns></returns>
public static IEnumerable<ProductRequest> CreateProductRequests(ImportMode mode = ImportMode.Insert)
{
    var prod = new ProductRequest
    {
        Sku = "SKU1",
        VariantSku = null,
        Name = "Test Product 1",
        Published = true,
        IsAvailable = true,
        PublishedOn = DateTime.Now,
        ImportMode = mode,
        Categories = new List<ProductCategoryRequest>
        {
            new ProductCategoryRequest
            {
                ExternalId = "TESTCATEGORY1",
                Name = "Test Category 1"
            },
            new ProductCategoryRequest
            {
                ExternalId = "TESTCATEGORY2",
                Name = "Test Category 2"
            }
        },
        Translations = new List<TranslationRequest>
        {
            new TranslationRequest
            {
                CultureInfoName = "en-US",
                DisplayName = "TEST EN PRODUCT DisplayName 2",
                LongDescription = "TEST EN PRODUCT LongDescription 2",
                ShortDescription = "TEST EN PRODUCT LongDescription 2"
            },
            new TranslationRequest
            {
                CultureInfoName = "nl",
                DisplayName = "TEST NL PRODUCT DisplayName 2",
                LongDescription = "TEST NL PRODUCT LongDescription 2",
                ShortDescription = "TEST NL PRODUCT LongDescription 2"
            }

        },
        Weight = 100,
        Tags = "Test",
        DiscountPercentage = 1,
        HasStockIndication = true,
        HasVariant = true,
        PropertyDefinitionName = "def product test",
        PriceCollection = new List<PriceRequest>
        {
            new PriceRequest
            {
                PriceDefinitionName = "EUR",
                UnitPrice = 99
            },
            new PriceRequest
            {
                PriceDefinitionName = "USD",
                UnitPrice = 88
            }
        },
        Variants = new[] {
            new ProductRequest
            {
                Sku = "SKU1",
                VariantSku = "VARIANTSKU1",
                Name = "Test Product 1",
                Published = true,
                IsAvailable = true,
                PublishedOn = DateTime.Now,
                ImportMode = mode,
                PriceCollection = new List<PriceRequest>
                {
                    new PriceRequest
                    {
                        PriceDefinitionName = "EUR",
                        UnitPrice = 99
                    },
                    new PriceRequest
                    {
                        PriceDefinitionName = "USD",
                        UnitPrice = 88
                    }
                },
                Translations = new List<TranslationRequest>
                {
                    new TranslationRequest
                    {
                        CultureInfoName = "en-US",
                        DisplayName = "TEST EN PRODUCT VARIANTSKU1",
                        LongDescription = "TEST EN PRODUCT LongDescription 2",
                        ShortDescription = "TEST EN PRODUCT LongDescription 2"
                    },
                    new TranslationRequest
                    {
                        CultureInfoName = "nl",
                        DisplayName = "TEST NL PRODUCT VARIANTSKU1",
                        LongDescription = "TEST NL PRODUCT LongDescription 2",
                        ShortDescription = "TEST NL PRODUCT LongDescription 2"
                    }

                },
                PropertyDefinitionName = "def product test",
                Properties = new List<PropertyValueRequest>
                {
                    new PropertyValueRequest
                    {
                        PropertyName = "test 1",
                        PropertyValue = "Test Product 1"
                    }
                }
            }
        },
        Inventories = new List<InventoryRequest>
        {
            new InventoryRequest
            {
                Stock = 100
            }
        },
        CreatedBy = "Unit test"
    };

    var prod2 = new ProductRequest
    {
        Sku = "SKU2",
        VariantSku = null,
        Name = "Test Product 2",
        Published = true,
        IsAvailable = true,
        PublishedOn = DateTime.Now,
        ImportMode = mode,
        Categories = new List<ProductCategoryRequest>
        {
            new ProductCategoryRequest
            {
                ExternalId = "TESTCATEGORY1",
                Name = "Test Category 1"
            },
            new ProductCategoryRequest
            {
                ExternalId = "TESTCATEGORY2",
                Name = "Test Category 2"
            }
        },
        Weight = 100,
        Tags = "Test 2",
        DiscountPercentage = 1,
        HasStockIndication = true,
        HasVariant = true,
        PropertyDefinitionName = "def product test",
        PriceCollection = new List<PriceRequest>
        {
            new PriceRequest
            {
                PriceDefinitionName = "EUR",
                UnitPrice = 99
            },
            new PriceRequest
            {
                PriceDefinitionName = "USD",
                UnitPrice = 88
            }
        },
        Variants = new[] {
            new ProductRequest
            {
                Sku = "SKU2",
                VariantSku = "VARIANTSKU2",
                Name = "Test Product 2",
                Published = true,
                IsAvailable = true,
                PublishedOn = DateTime.Now,
                ImportMode = mode,
                PropertyDefinitionName = "def product test",
                Properties = new List<PropertyValueRequest>
                {
                    new PropertyValueRequest
                    {
                        PropertyName = "test 1",
                        PropertyValue = "Test Product 2"
                    }
                },
                PriceCollection = new List<PriceRequest>
                {
                    new PriceRequest
                    {
                        PriceDefinitionName = "EUR",
                        UnitPrice = 99
                    },
                    new PriceRequest
                    {
                        PriceDefinitionName = "USD",
                        UnitPrice = 88
                    }
                },
                Inventories = new List<InventoryRequest>
                {
                    new InventoryRequest
                    {
                        Stock = 200
                    }
                },
                CreatedBy = "Unit test"
            }
        },
        CreatedBy = "Unit test"
    };

    return new[] { prod, prod2 };
}
```