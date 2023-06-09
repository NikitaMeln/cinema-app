![title-pic](title-pic.jpg)
# CINEMA APP

My web project is a model of an online cinema service. 
It allows creating the necessary pool of movies and cinema halls, 
as well as purchasing tickets for specific screenings. 

# Here's how it works. 
First, you need to log in. This model supports the registration 
and authentication of new users. After selecting a specific movie and screening, 
users can purchase tickets for cinema visits.
These tickets are added to the user's cart, and then the order is confirmed. 
By using this service, users can also access their order history. 
This model can be expanded and scaled according to the customer's needs.

## Project Structure

The project has the following structure:

    cinema

    --config

    --controller

    --dao

    --dto

    --exception

    --lib

    --model

    --service

    --util

    resources

# MODEL
**CinemaHall** - A cinema hall entity that has the fields capacity and 
description, describing the hall.

**Movie** - A movie entity that has the fields title for the movie title and 
description for the movie description.

**MovieSession** - A movie session entity that includes the entities Movie and 
CinemaHall, and the showTime field for the session date.

**Ticket** - A ticket for a specific movie session, which has the fields 
movieSession and the owner field, referring to the User.

**ShoppingCart** - An entity that belongs to a User and contains a list 
of selected tickets (List<Ticket>).

**Order** - This entity is associated with the ShoppingCart and includes a 
list of purchased tickets (List<Ticket>) and the orderTime field for the purchase time.

**Role** - Access rights assigned to a User. At this stage, there are 
two types of roles: USER and ADMIN.

**User** - An entity that stores information about a registered user, 
including email, password, and Role.

# DAO layer
The DAO layer is a collection of classes for accessing the database.
Each class corresponds to its entity and is implemented through its interface.
The SOLID principles are adhered to. This class is responsible solely for the 
database access logic. In this layer, methods for Creating, Reading, Updating, 
and Deleting entities (CRUD) from the database are implemented. When working with the 
database, the db.properties file needs to be configured in the "Setup" section.
The Service layer is responsible for executing the logic of the DAO layer.

# Service layer
The service layer is where the main business logic takes place before adding 
entities to the database.
The Service layer allows encapsulating logic, performing data checks and validation,
ensuring transactional integrity, error handling, and providing higher-level 
operations and functionality for other application components.
It contains the same CRUD methods as the DAO layer.

# DTO
The Data Transfer Object (DTO) layer is a layer in an application that is used for 
transferring data between different components of the system. It is designed to simplify 
and standardize the exchange of data between layers and application components.

The main purpose of the DTO layer is to define data objects that can be passed between 
different layers or components of the application without explicit coupling to the internal 
structure of the database or business objects. DTOs represent a simplified representation 
of data that can be transmitted over the network or between different services.

- **request**

A request in the DTO layer refers to the data object that is sent from one component 
to another to initiate a specific action or operation. It contains the necessary information 
and parameters required for the action to be performed.

- **response**

A response in the DTO layer is the data object that is returned as a result of a request. 
It encapsulates the data or information that is sent back from one component to another in 
a standardized format. 

# Controller layer
The Controller layer acts as the bridge between the user interface and the underlying business 
logic of the application. It receives and handles incoming requests from the client, processes them,
and provides the appropriate response.

## Example:

    for registration new user use this end point
    http://host_name/register

    for take response about user by mail use this and point
    http://host_name/by-email


It should be noted that this application has implemented secure access, which is divided into roles 
assigned to authenticated users.

To create new movies or cinema halls, a user must be authenticated as an "ADMIN".

To view the list of available movies, purchase tickets, and place orders, a user must have the "USER" role.

# lib layer
This layer contains classes for validating the entered user data, such as email and password.

# Technologies Used
This project utilizes the following technologies:

- Tomcat: Web server and servlet container
- Hibernate: Object-relational mapping framework
- Spring Security: Authentication and authorization framework
- Spring MVC: Model-View-Controller framework
- Git: Version control system
- Maven: Build and dependency management tool
- SQL: Structured Query Language for database operations

# Project Setup Instructions
To run this project locally, please follow these steps:

**Clone the repository:**

    git clone <repository-url>
Replace <repository-url> with the URL of the project's GitHub repository.

**Configure the Database:**
Locate the db.properties file in the project.
Open the file and set the necessary database configuration parameters such as
driver, url-db, username, and password.

**Build the Project:**
Ensure that Maven is installed on your system.
Open a command prompt or terminal.
Navigate to the project directory.
Run the following command to build the project:

    mvn clean install

**Deploy the Project:**
Deploy the project to a Tomcat server or any other compatible servlet container.
Copy the generated WAR file to the server's deployment directory.
Start the server to deploy the project.

**Access the Application:**
Once the server is running, open a web browser.
Enter the URL for accessing the application.
You should be able to see the home page of the cinema application.
Make sure to have the necessary dependencies and environment properly set up for running 
the project.

For any additional information or troubleshooting, refer to the project's documentation 
or contact the project maintainers.