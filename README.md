# School System
- **Production Build Status:** [![Build Status](https://jenkins.lamsaworld.com/buildStatus/icon?job=Lamsa-School-Service-Production-Pipline)](https://jenkins.lamsaworld.com/job/Lamsa-School-Service-Production-Pipline/)
- **Testing Build Status:** [![Build Status](https://jenkins.lamsaworld.com/buildStatus/icon?job=Lamsa-School-Service-Testing-Pipline)](https://jenkins.lamsaworld.com/job/Lamsa-School-Service-Testing-Pipline/) <br />
#### The school system facilitates educators in the development of customized learning materials for their students.

- For detailed API documentation, please refer to
  the [API Documentation](http://school-testing.lamsaworld.com/api/documentation).
- For comprehensive system documentation, please check
  the [System Documentation](https://docs.google.com/document/d/12v5BTRRuzksLnhRBEyZd4kJ_9gI5ttLGc9Z-o1xDgUI/edit?usp=sharing).

This system comprises two integral components:

- Data Service Layer: This RESTful back-end system manages the database, retrieves data, and seamlessly transmits it to
  both the front-end and mobile interfaces.
- User Interface: This component provides an intuitive client dashboard for teachers and schools to oversee and manage
  their learning materials.

## [System Components](docs/componentes.md)

### Authentication and Authorization

This component ensures secure access to the system. It handles user authentication, authorization, and role management,
allowing users to log in, maintain their profiles, and access appropriate features based on their roles

### Content Management

The content management component is responsible for creating, storing, and organizing educational materials.It
facilitates the creation of diverse educational materials, including a variety of learning content. This content can be
easily updated and retrieved as needed.

### Invitation System

The invitation system streamlines the onboarding process for new students. It manages invitations, validates user
requests, and facilitates the student invitation process, ensuring a smooth start for students joining the platform.

### Learning Paths

The learning paths component empowers educators to design and customize educational journeys for students. It allows for
the creation of structured learning paths, enabling students to progress through the curriculum in a logical sequence.

### School Management

This component handles information related to educational institutions. It supports school registration, profile
management, and administrative functions, Providing a centralized hub for school-related activities and individual
teacher activities, allowing efficient management and coordination.

### Student Management

The student management component focuses on student-related operations. It allows for student registration, profile
management, and progress tracking.

### Teacher Tools

The teacher tools component is designed to meet the needs of educators. It supports teacher registration, profile
management, and the creation and management of educational content. Teachers can use these tools to deliver effective
instruction to their students.

## [Architecture](docs/architecture.md)

![Architecture](https://lh3.googleusercontent.com/drive-viewer/AK7aPaCMu2qRQrNFra22HVfKqgfae5tAPWGHPKFdEKE3JSExxicmRYGg-OxauE-u_uvaR41HRaRO2OmHabaWRMmpl0SWUcuqdg=s1600)

### Repository Pattern

Our project follows the Repository Pattern, which is a design pattern that enhances data access and separation of
concerns within our application. With the Repository Pattern, we've structured our data access layer to use dedicated
repository classes. These repositories act as a bridge between our application's business logic and the data source,
providing a clean and organized way to manage data operations.

By adopting the Repository Pattern, we achieve several benefits, including:

- **Modularity**: Separating data access logic into repositories makes our codebase more modular and maintainable.

- **Testability**: It becomes easier to write unit tests for our application, as we can mock repository implementations
  to isolate data-related concerns.

- **Flexibility**: The Repository Pattern allows us to switch between different data storage mechanisms (e.g.,
  databases, APIs) with minimal changes to our business logic.

This architectural choice enhances the overall quality and maintainability of our codebase, making it more
developer-friendly and robust.

## [Technology Stack](docs/techstack.md)

### Front-End Framework: Vue.js

Our front-end is powered by Vue.js, a progressive JavaScript framework for building user interfaces. Vue.js enables us
to create interactive and dynamic web applications with ease.

### UI Library: Vuetify

We utilize Vuetify, a Material Design component framework, to build a sleek and responsive user interface. Vuetify
provides a rich set of pre-designed components and utilities, ensuring a consistent and visually appealing design across
our application.

### Repository Pattern

We've implemented the repository pattern to enhance data access and separation of concerns within our application. This
architectural choice allows us to manage data access through dedicated repository classes, making our codebase more
maintainable and testable.

### Spatie/Data

We leverage the Spatie/Data library to validate incoming requests as objects. This library streamlines request
validation by treating request data as objects, offering a cleaner and more organized approach to request handling.

### Spatie/Permission

Our application utilizes the Spatie/Permission library to manage user permissions and roles efficiently. This library
simplifies access control, making it easy to define and manage user roles and permissions, enhancing the security and
access control of our system.

## [Getting Started](docs/starting.md)

These instructions will help you set up and run the project on your local machine, specifically for development and
testing purposes.

## Prerequisites

Before getting started, ensure you have the following software and tools installed on your system:

- [Laravel](https://laravel.com) v9.52.10 via [Composer](https://getcomposer.org)
- [Node.js](https://nodejs.org) (latest version) via [npm](https://www.npmjs.com)
- PHP v8.0.2 or above
- An API testing tool like [Postman](https://www.postman.com)

## Installation

Follow these steps to set up the project:

1. Clone the repository to your local machine.
2. Create a `.env` file by copying `.env.example`.
3. Inside your new `.env` file, update the following configurations:

   ```plaintext
   DB_CONNECTION=mysql
   DB_HOST='your_database_host'
   DB_PORT='your_database_port'
   DB_DATABASE='your_database_schema_name'
   DB_USERNAME='your_database_username'
   DB_PASSWORD='your_database_password'

- Export the environment variables:

> - On MacOS/Linux, run the command: run command
    ````$ source .env ```` <br />
> - Windows : run the env.bat file

##  [Running the Project ](docs/running.md)

### With Docker (Local Machine)

1. Ensure you have Docker installed and running on your local machine.

2. After starting Docker, navigate to the project directory.

3. Build the Docker containers using one of the following commands:

   ```shell
   make build

Or

   ```shell
    docker-compose build
```

### To sync code changes between your machine and the container, add the following volume mounts to docker-compose-lamsa-school-service in your docker-compose.yml file:

- volumes:
  > ./storage/logs:/var/www/html/storage/logs <br />
  > ./app:/var/www/html/app <br />
  > ./public:/var/www/html/public <br />

### Apply code changes without restarting the container by running:

```sh
make npm-dev 
```

### Without Docker

#### Install Composer dependencies:

```sh
composer install 
```

Or

```sh
composer update 
```

##### Perform Laravel migration and seeding:

```sh
php artisan migrate:fresh --seed --seeder=PermissionSeeder
```

**_NOTE:_**

If you are confident that existing permissions won't conflict with PermissionSeeder.php, use:

```sh
php artisan migrate
```

#### To sync all permissions into the database, run:

```sh
php artisan permissions:sync
```

#### Set up Laravel Passport authentication:

```sh
php artisan passport:install
```

**_NOTE:_**
If you performed a fresh migration, run  ````passport:install ````again to generate Passport keys.

## [Running Laravel Tests](docs/testing.md)

To run tests for your Laravel application, use the following command:

```sh
php artisan test
