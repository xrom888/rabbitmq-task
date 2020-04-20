## Task
### Create simple random joke app 

We will create simple applications that will display random joke about programming.

How to get API access:
    - register on https://rapidapi.com/;
    - go to https://rapidapi.com/Sv443/api/jokeapi;
    - set category_name: 'Programming';
    - try it.

Two very simple applications needed:
1. Webservice that request jokes from Service #2 synchronously through RabbitMQ (for scalability reasons), return joke to UI client (browser) and add 
every joke that was sent to client as event to persisted RabbitMQ queue for further asynchronous processing by persistence services (this role will play Service #2).

2. Service that will:
    - request third-party API to get joke from https://rapidapi.com;
    - persist all update events asynchronously to some storage (file is ok here, but you can try Apache Kafka as ready to go event sourcing solution).

RabbitMQ roles:
    - gateway for requests (so Service #2 can be easily scaled);
    - queue for events that can be processed asynchronously.

On UI you just need very simple jQuery function that updates joke every 8 - 10 seconds.

How UI can looks like:

                                        Random Programming joke: 
        "Programming is 10% science, 20% ingenuity, and 70% getting the ingenuity to work with the science."