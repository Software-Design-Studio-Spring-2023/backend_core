# facial-recognition

I will be spitting this repo into two distinct components:

1. client

    This will be responsible for handling user input and rendering the output generated by the server.

2. server

    This will be responsible for:
        a. Training the model and generating a encoded file that will be used for facial recognition.
        b. Handling input from the client and running it through the facial_recognition package to detect faces, and serving the processed response back to the client

The client subrepo will be following clean architecture principles, which contains three components.
    ![Onion Architecture](https://miro.medium.com/v2/resize:fit:924/format:webp/1*0Pg6_UsaKiiEqUV3kf2HXg.png)

    a. domain

        The domain layer is the innermost layer of the architecture.

        The domain models and services will be inside this layer, containing all the business rules of the software. It should be purely logical, not performing any IO operations at all.

        As this layer is purely logical, it should be pretty easy to test it, as you don’t have to worry about mocking IO operations.

        This layer also cannot know about anything declared in the application or infrastructure layers

        It will contain any interfaces/schema definitions, business logic, but never any implementation or code logic.

    b. infrastructure

        This layer implements the business logic that is defined in the domain layer. 
        
        Generally you want to follow dependency inversion when making references to logic in another layer to make sure that the control flow of the application flows from the outside in i.e from gateway->infra->domain.

        ![Control Flow in Clean Architecture](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*jH0iI7-MSQYgLUrqTUm6mg.png)

    c. gateways

        This layer is easy. It contains any logic that is needed to communicate with services outside of the application.

        This is where you would implement your DB handling classes, authentication, CRUD etc