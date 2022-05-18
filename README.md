# pizza-jeff-vue

This is Jorge's challenge to create a web application for a pizzeria. It is my firs web aplication using VueJS

## Project description

The project consists of an application to manage the orders received by a pizzeria. I have made the application using the VueJS frame-work and the Bootstrap library/frame-work.

### Project parts

#### Pages 

I have divided the project into two pages, one where all the order management is done and the other where the order history is stored.
The page where the history of the orders has been made has been made with the only purpose of learning how to make routes and communications between different pages.

#### Componentes

The application has 5 components, including header and footer.
The other 3 components are: order renderers, order information and customer information.

### Features

The web application is responsive, I have only made a break point that divides between mobile or tablet and PC.
The application makes get requests to receive orders, and post requests to update the status of orders.
Via the links in the header you can navigate between the pages.

The structure of the homepage follows a Kanban board structure, where orders are sorted according to the time you want them to be delivered.
To sort them by date we have obtained the time from the date January 1, 1970 00:00:00:00 and used the native JavaScript sort() method.
A method has also been used to make the user's telephone number more readable as a string. 
Depending on the status of each order, it will appear in one of the three columns (To do, in progress, Done).

### Future possibilities

I have started to make an order finder in case the user needs to retrieve the information of an old order or an old customer.
This functionality is not finished as I believe that other aspects need to be prioritised.





## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Run your end-to-end tests
```
npm run test:e2e
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
