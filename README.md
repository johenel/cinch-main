## Summary
A simple test project (product-checkout-order with email notification) that is structured in micro service format and controlled in docker environment.

#### Architecture
- Micro service
#### Deployment
- Docker (v20)
#### Versioning System
- git
#### Backend
- Laravel (v12), PHP (v8.3), Redis, SMTP
#### Frontend
- Vue3, Javascript, Node (v21.6.1 or up), Typescript, CSS, TailwindCSS
#### Database
- MySQL (v8)
#### Automated Testing
- Backend: PHPUnit
- Frontend: Vitest


## Installation
Clone the repositories: 

- Main (Parent Directory) 

``git clone git@github.com:johenel/cinch-main.git``

Then go inside the main directory and clone the services repositories.

Product Service - ``git clone git@github.com:johenel/cinch-products.git`` <br>
Checkout Service - ``git clone git@github.com:johenel/cinch-checkout.git`` <br>
Mailer Service - ``git clone https://github.com/johenel/cinch-mailer`` <br>
Frontend Service - ``git clone git@github.com:johenel/cinch-frontend.git``

The folder structure should look like this:
- cinch-main
- - cinch-products
- - cinch-checkout
- - cinch-mailer
- - cinch-frontend

One confirmed, proceed with the following commands

```
    docker-compose build
    docker-compose up -d
```

When the docker build is done and started the services
make sure that all services are running using the script:

``docker ps``

This should list all running services and you should be able to see the following container names:
- cinch-frontend-1
- cinch-email-worker-1
- cinch-email-nginx-1
- cinch-checkout-nginx-1
- cinch-product-nginx-1
- cinch-email-1
- cinch-product-1
- cinch-checkout-1
- cinch-mailhog-1
- cinch-redis-1
- cinch-db-1

#### Once confirmed,  proceed creating databases with the following commands

```
    docker exec -it cinch-db-1 mysql -u root -p
    (pass: root)
    
    create database db_product;
    create database db_product_testing;
    create database db_checkout;
    create database db_checkout_testing;
    create database db_mailer;
    create database db_mailer_testing
```

Once database creation is completed, proceed setting up each services in the following order.
Each will have their own instruction that will end with running a unit test script and when the tests are good it means you can proceed to the next service.


Product Service
- https://github.com/johenel/cinch-products/blob/main/README.md

Checkout Service
- https://github.com/johenel/cinch-checkout/blob/main/README.md

Mailer Service
- https://github.com/johenel/cinch-mailer/blob/main/README.md

Frontend Service
- https://github.com/johenel/cinch-frontend/blob/main/README.md


<hr>
After completing all the services setup, you can now access it on

``localhost:80`` or `http://3.25.188.173/` for live testing.
