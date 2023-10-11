# Content Service
**Production Build Status:**

**[![Build Status](https://jenkins.lamsaworld.com/buildStatus/icon?job=Production-Content-Service-Pipline)](https://jenkins.lamsaworld.com/job/Production-Content-Service-Pipline-Pipline/)**

**Testing Build Status:**

[![Build Status](https://jenkins.lamsaworld.com/buildStatus/icon?job=Content-Service-Testing-Pipline)](https://jenkins.lamsaworld.com/job/Content-Service-Testing-Pipline/) <br />

This service handle everything related to Content, it's 
- Responsible for content listing, returning the content to the app and streaming content events.
- Handle the recommendation with GoogleML and AwsML.
- Handle the adaptive algorithm.


Check [API Documentation](https://api-testing.lamsaworld.com/v1/content/api/doc) -  for this service


## Getting Started

These instructions will help you set up and run the project on your local machine, specifically for development and
testing purposes.

## Prerequisites

Before getting started, ensure you have the following software and tools installed on your system:

- [Symfony](https://symfony.com) v3.4 via [Composer](https://getcomposer.org)
- PHP v7.1
- An API testing tool like [Postman](https://www.postman.com)

## Installation

Follow these steps to set up the project:

1. Clone the repository to your local machine.
2. Create a `.env` file by copying `.env.example`.
3. Inside your new `.env` file, update the following configurations:

   ```plaintext
    DB_HOST='Put the host'
    DB_PASSWORD='Put the password'
    DB_NAME=content
    DB_PORT=3306
    DB_USER='Put the user name'
    JWT_KEY_PASS_PHRASE=
    JWT_TOKEN_TTL=
    SYMFONY_ENV=dev
    CONTENT_PRIVATE_KEY=''
    KEY_PAIR_ID=''
    CONTENT_RECOMMENDATION_ARN='arn:aws:personalize:us-east-1:***************'
    SECTION_RECOMMENDATION_ARN='arn:aws:personalize:us-east-1:***************'
    SECTION_CONTENTS_RANK_ARN='arn:aws:personalize:us-east-1:***************'
    CAMPAIGN_CONTENT_ARN='arn:aws:personalize:us-east-1:***************'
    CAMPAIGN_SECTION_ARN='arn:aws:personalize:us-east-1:***************'
    FILTER_CONTENT_ARN='arn:aws:personalize:us-east-1:***************'
    FILTER_SECTION_ARN='arn:aws:personalize:us-east-1:***************'
    CAMPAIGN_TREND_ARN='arn:aws:personalize:us-east-1:***************'
    AWS_KEY='***************'
    AWS_SECRET='***************'
    BUCKET_NAME=''
    GOOGLE_PREDICTION_SECRET='***************'
    GOOGLE_APPLICATION_CREDENTIALS='***************'
- Export the environment variables:
> - On MacOS/Linux, run the command: run command
    ````$ source .env ```` <br />
> - Windows : run the env.bat file
> * make sure your variables are sourced by running this command ```echo $DB_HOST```
#### Install Composer dependencies:
```sh
composer install 
```

Or

```sh
composer update 
```

## Running the Project

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
### With Symfony Server (Local Machine)
Run the following to start symfony server
  ```shell 
$ php bin/console server:start
```

## Running Tests

To run tests for your Symfony application, use the following command:

```sh
run this command ```./vendor/bin/phpunit ```
