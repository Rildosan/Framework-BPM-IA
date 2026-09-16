# Fourth Coffee

A sample ontology representing a modern coffee shop chain with suppliers, products, stores, customers, and orders.

## **Grafo de Ontologia do Processo**

<img src="file:///C:/Users/rildo/AppData/Roaming/marktext/images/2026-09-16-09-18-53-fourth-coffee-graph%20(1).png" title="" alt="" width="509"> 



## Entities

### 👤 Customer

A person who purchases coffee products from our stores

**Properties:**

- **customerId** (string) (identifier): Unique customer identifier
- **name** (string): Full name of the customer
- **email** (string): Contact email address
- **loyaltyTier** (enum): Loyalty program tier
- **joinDate** (date): Date the customer joined
- **totalSpend** (decimal): Lifetime spend amount

### 🧾 Order

A customer purchase transaction at a store

**Properties:**

- **orderId** (string) (identifier): Unique order identifier
- **timestamp** (datetime): When the order was placed
- **total** (decimal): Total order amount
- **status** (enum): Current order status
- **paymentMethod** (enum): Payment method used

### ☕ Product

A coffee product or item available for sale

**Properties:**

- **productId** (string) (identifier): Unique product identifier
- **name** (string): Product name
- **category** (enum): Product category
- **price** (decimal): Unit price
- **origin** (string): Coffee bean origin country
- **isOrganic** (boolean): Whether the product is certified organic

### 🏪 Store

A physical coffee shop location

**Properties:**

- **storeId** (string) (identifier): Unique store identifier
- **name** (string): Store name
- **city** (string): City location
- **state** (string): State/Province
- **openDate** (date): Store opening date
- **capacity** (integer): Seating capacity

### 🚚 Supplier

A coffee bean or goods supplier partner

**Properties:**

- **supplierId** (string) (identifier): Unique supplier identifier
- **name** (string): Supplier company name
- **country** (string): Country of operation
- **certification** (enum): Sustainability certification
- **rating** (decimal): Quality rating (1-5)

### 📦 Shipment

A delivery of goods from supplier to store

**Properties:**

- **shipmentId** (string) (identifier): Unique shipment identifier
- **dispatchDate** (date): Date shipped from supplier
- **arrivalDate** (date): Date arrived at store
- **status** (enum): Shipment status
- **weight** (decimal): Total shipment weight

## Relationships

### places

**Customer** → **Order** (one-to-many)
A customer places one or more orders

### contains

**Order** → **Product** (many-to-many)
An order contains one or more products

### processedAt

**Order** → **Store** (many-to-one)
An order is processed at a specific store

### sourcedFrom

**Product** → **Supplier** (many-to-one)
A product's ingredients are sourced from a supplier

### sentBy

**Shipment** → **Supplier** (many-to-one)
A shipment is sent by a supplier

### deliveredTo

**Shipment** → **Store** (many-to-one)
A shipment is delivered to a store

### carries

**Shipment** → **Product** (many-to-many)
A shipment carries products
