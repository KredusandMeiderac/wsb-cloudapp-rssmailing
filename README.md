link do strony: https://rssmailcis.azurewebsites.net/
Save xml tvn24:
![image](https://user-images.githubusercontent.com/55463732/116046575-80f63100-a673-11eb-9205-4ba8fbf17942.png)

Preview:
![image](https://user-images.githubusercontent.com/55463732/116046656-94a19780-a673-11eb-8405-b1eaed8e98db.png)

Send:
![image](https://user-images.githubusercontent.com/55463732/116046698-a08d5980-a673-11eb-95ac-d32eaf4dc314.png)

Email:
![image](https://user-images.githubusercontent.com/55463732/116046784-b438c000-a673-11eb-86d9-408567d41ba1.png)



# Feedmail

WebApp wrote in node js and vanilla js for sending rss via email

## Installation

Run npm installation command in the project root folder

```bash
npm i
```

## Run on the local machine

To run on the local machine enter command in the project root folder

```bash
npm run start:dev
```

## Run on Azure
1. Create AppService and configure deployment using Github actions.
2. Create CosmosDb with mongo client API in version 3.x
3. Wait until provisioning of the services will finish
4. Enter in AppService go to Configuration.
5. You should be seeing *Application settings* and *Connection strings* sections
6. Add two environment variables in section *Application settings*
- NODE_ENV with value production
- NODE_CONFIG with value

      {
          "feedmail": {
              "db": {
                  "url": "", 
                  "name": "prod", 
                  "options": {
                  "useUnifiedTopology": true 
                  }
              },
              "logger": {
                  "level": "debug",
                  "filename": "./backend.log"
              },
              "mailgun": {
                  "domain": "",
                  "apiKey": ""
              }  
          }
      }

**Remark**

Notice there are empty fields in this config:
- url - you need to copy-paste the connection string of the newly created CosmosDb. The connection string is visible in the Configuration section in the CosmosDb,
- apiKey - you need to create an account in mailgun portal. You will get an API key after login into mailgun portal,
- domain - if you don't have a domain you can use the sandbox domain created on mailgun web page. For more info go see mailgun documentation page.
