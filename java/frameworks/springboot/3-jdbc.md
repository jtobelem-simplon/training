# Configure jdbc using spring-boot : easy

#### Initialization

- Start a new gradle project (remove all useless)
- add dependencies : spring-boot-starter-web (2.1), spring-boot-starter-jdbc (2.1) and mysql-connector-java (5.1.47)
- add a source folder /src/main/resources :

![resources folder](img/resources-folder.png)

- and a file application.properties into that folder :

```
spring.jpa.hibernate.ddl-auto=create
spring.datasource.url=jdbc:mysql://localhost:3306/db_example?useSSL\=false
spring.datasource.username=root
spring.datasource.password=
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
  ```

#### Database

Create an empty shema named db_example in your mysql database. Check your password in application.properties.

#### Model

- Create a simple class Customer in the package model :

![customer](img/customer.png)

#### Application

- Create a class Application :

```java
package customers;

import java.text.MessageFormat;
import java.util.Arrays;
import java.util.List;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.jdbc.core.JdbcTemplate;

@SpringBootApplication
public class Application implements CommandLineRunner {

    private static final Logger log = LoggerFactory.getLogger(Application.class);

    public static void main(String args[]) {
        SpringApplication.run(Application.class, args);
    }

    @Autowired
    JdbcTemplate jdbcTemplate;

    @Override
    public void run(String... strings) throws Exception {
    	createTable();
    	insertValues();
    }

    public void insertValues() {
      log.info("Insert new customers in database");

      // TODO create and insert customers
    }

    public void createTable() {
    	 log.info("Creating tables");

       // TODO create tables if not already exist
    }

    /**
     * @param newCusto : the Customer to be added in database
     */
    public void insertCustomer(Customer newCusto) {
    	jdbcTemplate.update(
    			"INSERT INTO customers(first_name, last_name) VALUES (?,?)",
    			newCusto.getFirstName(),
    			newCusto.getLastName()
    			);
    }

}
```
> The class implements CommandLineRunner, and will launch a run method when the server will be started and ready
> The application declares a jdbcTemplate with the annotation @Autowired : this jdbcTemplate will be automagically initialized by spring

- Use the idbcTemplate to create the table customers with the sql instruction : `CREATE TABLE customers(id SERIAL, first_name VARCHAR(255), last_name VARCHAR(255))`
- In a the method insertValues(), create the customers : "John Woo","Jeff Dean","Josh Bloch and "Josh Long". Use the insertCustomer method to add them in database.

#### Refactor the code and move all queries in same place

- Create a package repository and inside a CustomerRepository class :

```java
package customers.repository;

import java.util.Arrays;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Repository;



@Repository
public class CustomerRepository {

	@Autowired
	JdbcTemplate jdbcTemplate;


	public void createTable() {
		// TODO create customers table
	}

	/**
	 * Create 4 Customers
	 */
	public void insertValues() {
	   // TODO create 4 Customer Objects, and add it in database
	}

	/**
	 * @param newCusto : the Customer to be added in database
	 */
	public void insertCustomer(Customer newCusto) {
		jdbcTemplate.update(
				"INSERT INTO customers(first_name, last_name) VALUES (?,?)",
				newCusto.getFirstName(),
				newCusto.getLastName()
				);
	}

}
```

> The class have @Repository annotation so Spring can find it when using @Autowired from an other place.
> You can now move all queries from the Application and place it in the Repository
> Finally you will declare your Repository in the Application as @Autowired :

```java
@Autowired
	private CustomerRepository customerRepository;

	@Override
	public void run(String... strings) throws Exception {
		log.info("Creating tables");
		customerRepository.createTable();

		log.info("Insert new customers in database");
		customerRepository.insertValues();

	}
```

#### Mapping into objects the result of queries
- Create a class CustomerRowMapper :

```java
package customers.repository;

import java.sql.ResultSet;
import java.sql.SQLException;

import org.springframework.jdbc.core.RowMapper;

public class CustomerRowMapper implements RowMapper<Customer>{

	@Override
	public Customer mapRow(ResultSet rs, int rowNum) throws SQLException {
		return new Customer(rs.getLong("id"), rs.getString("first_name"), rs.getString("last_name"));
	}


}
```

- Use it in a method findBySurname. This method is to be placed in the Repository class :

```java
public List<Customer> findBySurname(String surname){
    	 log.info(MessageFormat.format("Querying for customer records where first_name = {0}:", surname));

         return jdbcTemplate.query(
                 "SELECT id, first_name, last_name FROM customers WHERE first_name = ?", new Object[] {surname },
                 new CustomerRowMapper());
    }
```

- test this method in the run method of the Application to log all Customer whose surname is "Josh"

#### Controller

- Add a method findAll in the repository :

```java
public List<Customer> findAll(){
    	 // TODO
    }
```
- Create a CustomerController in a package controller with a mapping for the route /customers. Annote with @RestController :

```java
package customers.controller;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class CustomerController {

	@RequestMapping("/customers")
	public List<Customer> findAll(){
		// TODO
	}
}
```

#### Test it! [http://localhost:8080/customers](http://localhost:8080/customers)

#### [retour](td.md)
