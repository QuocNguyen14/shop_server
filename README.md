# Shop Server

## Introduction

The **Shop Server** project is a backend REST API built with **Node.js** and **Express.js**, utilizing **Sequelize ORM** with **MySQL**. Key features:

- **User authentication** with JWT
- **Product, category, post, and user management**
- **Role-based access control (RBAC)** with granular permissions
- **Image upload & processing** with Multer & Sharp
- **Automated job scheduling** using node-cron
- **Data pagination** with express-paginate
- **Access log tracking** for authentication events

## Installation

```sh
git clone https://github.com/QuocNguyen14/shop_server.git
cd shop_server
npm install
```

Configure environment variables in `.env` based on `.env.example`.

Run migrations and seed data:

```sh
npx sequelize-cli db:migrate
npx sequelize-cli db:seed:all
```

Start the server:

```sh
npm start
```

## Technologies Used

- **Node.js + Express.js**
- **Sequelize ORM + MySQL**
- **JWT (jsonwebtoken)**
- **Multer + Sharp** (Image upload & processing)
- **Node-cron** (Scheduled tasks)
- **Express-validator** (Data validation)
- **bcrypt** (Password hashing)

## API Endpoints

All protected routes require `Authorization: Bearer <token>` header.

### Auth
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| POST | `/api/login` | No | Login, returns JWT token |
| PUT | `/api/logout` | Yes | Logout, invalidates token |

### Users
| Method | Endpoint | Permission | Description |
|--------|----------|------------|-------------|
| GET | `/api/user-shows` | Yes | List all users |
| GET | `/api/user-show` | Yes | Get user by ID |
| POST | `/api/user-create` | USER_CREATE | Create user |
| PUT | `/api/user-update` | USER_UPDATE | Update user |
| DELETE | `/api/user-destroy` | USER_DESTROY | Delete user |
| PUT | `/api/users/:userId/approve` | APPROVE_USER | Approve user |

### Roles & Permissions
| Method | Endpoint | Permission | Description |
|--------|----------|------------|-------------|
| GET | `/api/role-shows` | Yes | List all roles |
| POST | `/api/role-create` | ROLE_CREATE | Create role |
| PUT | `/api/role-update` | ROLE_UPDATE | Update role |
| DELETE | `/api/role-destroy` | ROLE_DESTROY | Delete role |
| GET | `/api/permission-shows` | Yes | List all permissions |
| POST | `/api/permissions-create` | PERMISSIONS_CREATE | Create permission |
| PUT | `/api/permissions-update/:id` | PERMISSIONS_UPDATE | Update permission |
| DELETE | `/api/permissions-delete/:id` | PERMISSIONS_DELETE | Delete permission |

### Products
| Method | Endpoint | Permission | Description |
|--------|----------|------------|-------------|
| GET | `/api/product-show` | No | List products (paginated) |
| GET | `/api/product-show/:slug` | No | Get product by slug |
| GET | `/api/product-show-with-priority` | No | List products by priority |
| POST | `/api/product-create` | PRODUCT_CREATE | Create product |
| PUT | `/api/product-update/:id` | PRODUCT_UPDATE | Update product |
| DELETE | `/api/product/:id` | PRODUCT_DELETE | Delete product |

### Categories
| Method | Endpoint | Permission | Description |
|--------|----------|------------|-------------|
| GET | `/api/categories/public` | No | List public categories |
| GET | `/api/categories` | CATEGORY | List all categories |
| GET | `/api/categories/:id` | Yes | Get category by ID |
| POST | `/api/categories` | CATEGORY_CREATE | Create category |
| PUT | `/api/categories/:id` | CATEGORY_UPDATE | Update category |
| DELETE | `/api/categories/:id` | CATEGORY_DELETE | Delete category |

### Posts
| Method | Endpoint | Permission | Description |
|--------|----------|------------|-------------|
| GET | `/api/posts` | No | List all posts |
| GET | `/api/posts/:id` | No | Get post by ID |
| POST | `/api/blog-posts-create` | POST_CREATE | Create blog post with image |
| PUT | `/api/posts-update/:id` | POST_UPDATE | Update post |
| DELETE | `/api/posts-delete/:id` | POST_DELETE | Delete post |

### Companies (Partners)
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| GET | `/api/company-shows` | No | List all companies |
| POST | `/api/company-create` | Yes | Create company with logo |
| PUT | `/api/company-update-by-id/:id` | Yes | Update company info |
| DELETE | `/api/company-delete/:id` | Yes | Delete company |

### Media
| Method | Endpoint | Permission | Description |
|--------|----------|------------|-------------|
| GET | `/api/get-media` | Yes | List media files |
| POST | `/api/upload-media` | Yes | Upload media file |
| PUT | `/api/update-media/:id` | MEDIA_UPDATE | Update media |
| DELETE | `/api/delete-media/:id` | MEDIA_DELETE | Delete media |

## License

Developed by **QuocNguyen**.
