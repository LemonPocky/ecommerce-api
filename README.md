# E-commerce API
API for an (pseudo) ecommerce site that can store products and add tags.

--- 

## Features
- View, add, edit, and delete products
- View, add, edit, and delete product categories
- View, add, edit, and delete product tags
- View products with their tags and categories in one GET call

---

## Requirements
- [Node/npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- [MySQL](https://dev.mysql.com/downloads/mysql/)
- [Any API Client such as Insomnia](https://insomnia.rest/download)

---

## Installation
1. Clone the repo or download the code as a zip.   
```
git clone https://github.com/LemonPocky/ecommerce-api.git
```
2. If downloaded as zip, unzip the contents. Place the folder in an easily accessible location on your computer.
3. Install MySQL if necessary. Import schema.sql into MySQL to create the database.
```
mysql -u <username> -p employee_cms_db < db/schema.sql
```

4. Make a copy of ".env.EXAMPLE" and rename it to ".env". Fill out the username and password details.
5. While in the root folder, run "npm install", followed by "npm run seed" to seed the database with placeholder data.
```
npm install
npm run seed
```
*Note: You do not need to run seed if you have your own data to insert into the database.*

6. Start the API server.
```
npm start
```

---

## Usage

[See a video demo of the API here](https://streamable.com/13yi58)

## Products

> GET /api/products

Returns all products. Returns an empty array if there are no proudcts.

> GET /api/products/:id

Returns one product by id. Returns a 404 error if there is no product with that id.

> POST /api/products

Insert a new product into the database. Allowable fields are:
```
{
  "product_name": "String",
  "price": Number,
  "stock": Number,
  "category_id": Number,
  "tagIds": [Number]
}
```
Returns an array of tag-product associations created for the product.

> PUT /api/products/:id

Update an existing product in the database. Allowable fields are the same as POST. Returns a Sequelize error if there is no product with that id. (Known issue)

> DELETE api/products/:id

Delete a product in the database. Returns 1 if a product is deleted and 0 if no product was deleted or it does not exist.

## Categories

> GET /api/categories

Returns all categories. Returns an empty array if there are no categories.

> GET /api/categories/:id

Returns one category by id. Returns a 404 error if there is no category with that id.

> POST /api/categories

Insert a new category into the database. Allowable fields are:
```
{
  "category_name": "String"
}
```
Returns the newly created category object.

> PUT /api/categories/:id

Update an existing category in the database. Allowable fields are the same as POST. Returns 1 if a category is deleted and 0 if no category was deleted or it does not exist.

> DELETE api/categories/:id

Delete a category in the database. Returns 1 if a category is deleted and 0 if no category was deleted or it does not exist.

## Tags

> GET /api/tags

Returns all tags. Returns an empty array if there are no tags.

> GET /api/tags/:id

Returns one tag by id. Returns a 404 error if there is no tag with that id.

> POST /api/tags

Insert a new tag into the database. Allowable fields are:
```
{
  "tag_name": "String"
}
```
Returns the newly created tag object.

> PUT /api/tags/:id

Update an existing tag in the database. Allowable fields are the same as POST. Returns 1 if a tag is deleted and 0 if no tag was deleted or it does not exist.

> DELETE api/tags/:id

Delete a tag in the database. Returns 1 if a tag is deleted and 0 if no tag was deleted or it does not exist.