
# Specification to API of Productions

The resource is **/products** (representation the model).

### POST /api/v1/products

**Payload**:

```json 
{
  "sku": 43264,
  "name": "L'Oréal Professionnel Expert Absolut Repair Cortex Lipidium - Máscara de Reconstrução 500g",
  "inventory":{
    "warehouses":[
      {
        "locality": "SP",
        "quantity": 12,
        "type": "ECOMMERCE"
      },
      {
        "locality": "MOEMA",
        "quantity": 3,
        "type": "PHYSICAL_STORE"
      }
   ]
  }
}
```

**Rules**:

- **SKU** not informed or invalid value return 400;
- **Name** not informed or empty value return 400;
- **Inventory** not informed return 400;
- **Warehoures** not informed or empty list return 400;
- **Locality** not informed or empty value return 400;
- **Quantity** not informed return 400;
- **Type** not informed return 400;
- **SKU** already exist return 409;
- **Locality** invalid (enumeration) return 412;
- **Type** invalid (enumeration) return 412;
- Success return 201 with uri in location insert on header.

### PATCH /api/v1/products/${sku}

**Payload**:

```json
{
  "name": "L'Oréal Professionnel Expert Absolut Repair Cortex Lipidium - Máscara de Reconstrução 500g",
}
```

**Or**

```json
{
  "inventory":{
    "warehouses":[
      {
        "locality": "SP",
        "quantity": 12,
        "type": "ECOMMERCE"
      },
      {
        "locality": "MOEMA",
        "quantity": 3,
        "type": "PHYSICAL_STORE"
      }
    ]
  }
}
```

**Rules**:

- **SKU** not informed or invalid value return 400;
- **SKU** not found return 404;
- **Name** not informed or empty value return 400;
- **Inventory** not informed return 400;
- **Warehoures** not informed or empty list return 400;
- **Locality** not informed or empty value return 400;
- **Quantity** not informed return 400;
- **Type** not informed return 400;
- **Locality** invalid (enumeration) return 412;
- **Type** invalid (enumeration) return 412;
- **Success** returned 204.

### GET /api/v1/products/${sku}

**Response**:

```json
{
  "sku": 43264,
  "name": "L'Oréal Professionnel Expert Absolut Repair Cortex Lipidium - Máscara de Reconstrução 500g",
  "inventory":{
    "quantity":15,
    "warehouses":[
      {
        "locality": "SP",
        "quantity": 12,
        "type": "ECOMMERCE"
      },
      {
        "locality": "MOEMA",
        "quantit": 3,
        "type": "PHYSICAL_STORE"
      }
    ]
  },
  "isMarketable": true
}
```

**Rules:**
- **SKU** not informed or invalid value return 400;
- **SKU** not found return 404;
- Success returned 200 with response above information.

### DELETE /api/v1/products/${sku}

**Rules:**
- **SKU** not informed or invalid value return 400;
- **SKU** not found return 404;
- Success returned 204.

__Ref__:
- https://docs.microsoft.com/pt-br/azure/architecture/best-practices/api-design
- https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status


