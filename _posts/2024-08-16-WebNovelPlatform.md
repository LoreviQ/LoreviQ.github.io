---
layout: post
title: WebNovelClient: Building a Scalable Platform for Hosting and Sharing Written Works
tags: [go, javascript, api, react, ci/cd]
comments: false
---

[**Github Link**](https://github.com/LoreviQ/WebNovelPlatform)

WebNovelClient is a full-stack project designed to showcase my technical skills across various domains, including backend API development, frontend design, and CI/CD. Inspired by my passion for writing, I created this platform to enable users to share and host written works. 

You can explore a live demo of the project here: [https://webnovelclient-y5hewbdc4a-nw.a.run.app/](https://webnovelclient-y5hewbdc4a-nw.a.run.app/). 

The application is hosted on Google Cloud Platform (GCP) with minimal resources for demonstration purposes, so you may experience some latency. This is a limitation of the current server configuration, not the underlying code. Feel free to create an account and explore the platform’s features.

## Key Technologies and Methodologies

In building WebNovelClient, I chose a combination of modern technologies and methodologies to create a robust, scalable, and efficient platform. My decisions were influenced by a desire to learn new skills, research on industry standards, and the availability of cost-effective resources. Below is an overview of the key technologies used and the rationale behind each choice:

#### 1. Backend Development with Go
- **Why Go?**  
  Go (or Golang) was chosen for the backend due to its strong performance, simplicity, and concurrency model. Known for its efficiency, Go is particularly well-suited for building high-performance web applications and APIs. Its lightweight goroutines allow for efficient management of concurrent tasks, which is ideal for handling multiple user requests simultaneously.
- **Benefits:**
  - **Performance:** Go's compiled nature and low-level capabilities result in fast execution times, making it an excellent choice for building APIs that need to serve data quickly.
  - **Simplicity:** Go's syntax is straightforward, making it easier to write and maintain clean, readable code. This was important for ensuring that the codebase remains manageable as the project grows.
  - **Strong Typing and Error Handling:** Go's strong typing system and emphasis on explicit error handling help reduce bugs and increase code reliability.

#### 2. Frontend Development with React
- **Why React?**  
  React was selected for the frontend due to its component-based architecture, which promotes reusability and modularity. React's popularity and active community also mean that there are abundant resources and libraries available to extend its functionality.
- **Benefits:**
  - **Component-Based Architecture:** React's component-based structure allowed me to build reusable UI components, which made development more efficient and the application more maintainable.
  - **Virtual DOM:** React's Virtual DOM optimizes updates to the user interface, ensuring a smooth and responsive user experience, even in complex applications.
  - **Rich Ecosystem:** React's vast ecosystem of tools and libraries enabled me to implement features like routing, state management, and theming with ease.

#### 3. Database Management with SQLite and Turso
- **Why SQLite and Turso?**  
  Turso was chosen as the cloud provider for its cost-effective hosting options, which were particularly attractive for a demonstration project. However, Turso exclusively supports libSQL, a fork of SQLite, which dictated my choice of database engine. While SQLite is lightweight and easy to set up, I encountered several limitations that made me wish I had used PostgreSQL instead, especially as the project grew in complexity.
- **Benefits:**
  - **Cost-Effectiveness:** Turso’s free tier allowed me to deploy and manage the database without incurring significant costs, which was ideal for a budget-conscious project.
  - **Simplicity:** SQLite’s serverless nature made it straightforward to implement, especially in the early stages of development. It’s self-contained, requiring minimal configuration, which suited the initial scope of the project.
- **Challenges:**
  - **Limitations of SQLite:** As the project progressed, I encountered challenges with SQLite’s limited concurrency support and lack of advanced features like complex querying and indexing, which PostgreSQL could have handled more efficiently.
  - **Provider Constraints:** My choice of Turso as a cloud provider limited my database options to libSQL, which, while functional, didn’t meet all the needs of the project as it scaled.

#### 4. CI/CD with GitHub Actions
- **Why GitHub Actions?**  
  GitHub Actions was chosen for Continuous Integration (CI) and Continuous Deployment (CD) due to its deep integration with GitHub repositories, ease of setup, and extensive community support.
- **Benefits:**
  - **Automated Testing and Deployment:** GitHub Actions enabled me to automate the testing and deployment process, ensuring that only tested and verified code is deployed to production. This reduces the risk of introducing bugs and keeps the application stable.
  - **Scalability:** As the project grows, GitHub Actions can easily scale to accommodate more complex workflows, such as multi-environment deployments or integration with other services.
  - **Cost-Effectiveness:** GitHub Actions provides a generous free tier, which allowed me to implement CI/CD without additional costs, keeping the project within budget.

#### 5. Test-Driven Development (TDD)
- **Why TDD?**  
  I implemented Test-Driven Development to ensure that the code is reliable and that new features do not break existing functionality. By writing tests before the actual code, I was able to clearly define the expected behavior of each component and function.
- **Benefits:**
  - **Code Reliability:** TDD helped catch bugs early in the development process, reducing the likelihood of issues in production.
  - **Refactoring Confidence:** With a robust suite of tests in place, I could refactor the codebase confidently, knowing that any breaking changes would be detected immediately.
  - **Documentation:** The tests themselves serve as a form of documentation, providing clear examples of how each part of the code is expected to behave.

#### 6. Cloud Hosting with Google Cloud Platform (GCP)
- **Why GCP?**  
  Google Cloud Platform was selected for hosting the application due to its flexibility, scalability, and the availability of a generous free tier, making it an ideal choice for deploying a demonstration project.
- **Benefits:**
  - **Scalability:** GCP offers the ability to scale resources as needed, which is crucial for future growth and handling increased traffic.
  - **Cost-Effectiveness:** The free tier allowed me to deploy the application without incurring significant costs, making it accessible for demonstration purposes.
  - **Integration with CI/CD:** GCP integrates well with CI/CD pipelines, enabling seamless deployments from GitHub Actions.
  - **Seamless Integration:** By hosting the frontend, backend API, and image uploads all within GCP, the integration between these components is simplified. GCP’s services are designed to work together seamlessly, reducing the complexity of cross-service communication and ensuring faster, more reliable interactions between the client, API, and storage.

#### Summary of Technology Choices
Each technology and tool used in WebNovelClient was chosen with a balance of learning opportunities, research into industry best practices, and budget considerations in mind. Together, they contribute to a robust, maintainable, and scalable application that serves as a testament to my development skills and adaptability.

## Deployment Architecture Overview

WebNovelClient is composed of three main components: the frontend client, the backend API, and the database. Each of these components is deployed and managed in a way that ensures smooth interaction and efficient data handling.

- **Frontend (React App):**  
  The frontend client is built with React and hosted on Google Cloud Platform (GCP). It serves as the user interface, allowing users to interact with the platform. The client makes HTTP requests to the backend API to fetch or submit data.

- **Backend (API):**  
  The API is developed in Go and is also hosted on GCP. It acts as the intermediary between the frontend client and the database. When the frontend makes a request, the API processes it, interacts with the database if needed, and returns the appropriate response to the client. This includes handling user authentication, managing content, and generating signed URLs for image uploads.

- **Database (Turso with libSQL):**  
  The database is hosted on Turso and uses libSQL, a fork of SQLite. It stores all the essential data, such as user information, written works, and metadata about the images. However, due to the limitations of SQLite, images themselves are not stored directly in the database.

- **Image Storage (GCP Cloud Storage):**  
  For image storage, GCP’s Cloud Storage is used. When a user uploads an image, the following process occurs:
  1. The frontend client sends a request to the API indicating that an image needs to be uploaded.
  2. The API generates a signed URL from GCP Cloud Storage and returns it to the client.
  3. The client uploads the image directly to the GCP bucket using the signed URL.
  4. The client then sends the image URL back to the API, which stores this URL in the database.

#### Visualizing the Architecture

Here’s a simplified diagram of the deployment architecture:

    [Frontend Client (React)]  <-->  [Backend API (Go)]  <-->  [Database (Turso, libSQL)]
        |                                      |
        |                                      |
        +--> [GCP Cloud Storage (Images)] <---+
    
- **Flow of Data:**
  - **Frontend to Backend:** The client sends requests (e.g., user data, content) to the API.
  - **Backend to Database:** The API interacts with the database to retrieve or store data.
  - **Backend to GCP Cloud Storage:** For image uploads, the API generates a signed URL and facilitates image storage.

This architecture ensures that the platform is modular, scalable, and able to handle various data types efficiently. Hosting both the frontend and backend on GCP simplifies deployment and integration, while using Turso for the database and GCP Cloud Storage for images balances cost with functionality.

#### Scalability and Future-Proofing with Separate API and Client

Splitting the frontend client and backend API into distinct components provides significant advantages for scalability and resource management. This separation allows each component to be scaled independently based on its specific needs and load, optimizing resource usage and performance.

- **Independent Scaling:**  
  By decoupling the frontend client from the backend API, you can scale each component independently. For example, if the API experiences increased traffic or processing demands, you can allocate additional resources specifically to the API without affecting the frontend client. Conversely, if the client side needs to handle more user interactions or load, it can be scaled separately.

- **Resource Optimization:**  
  This separation ensures that resources are utilized efficiently. You avoid the inefficiency of scaling both the client and API together when only one is under increased load. This means you can optimize costs and performance by allocating resources precisely where they are needed.

- **Flexibility in Deployment:**  
  Separate deployments allow for more flexibility. For instance, you can deploy updates or improvements to the API without requiring simultaneous updates to the client, and vice versa. This modular approach simplifies development cycles and reduces the risk of introducing bugs or downtime in unrelated parts of the application.

- **Future Expansion with Kubernetes:**  
  Although Kubernetes is not used in this demonstration project, it is a powerful tool worth considering for future iterations, especially as the project scales. Kubernetes excels in managing large-scale applications with multiple containers, offering benefits such as automated scaling, efficient resource management, seamless rollouts with automatic rollbacks, and self-healing capabilities. However, for this demonstration project, which operates with a single container, the complexity and overhead of Kubernetes would be unnecessary. Its primary advantages come into play when managing more extensive deployments, which is beyond the current scope. Nonetheless, understanding how Kubernetes could be integrated into a real-world version of the project shows a readiness to leverage advanced tools for scalable and efficient application management as the project evolves.

## Backend Development

#### Main

The API codebase is organized within the ./api folder on GitHub. The main entry point initializes and serves the server, with each endpoint managed by dedicated handler functions. A handler function decodes the request, performs an action, and returns a response. For example, the handler function postUser is the following:


    func (cfg *apiConfig) postUser(w http.ResponseWriter, r *http.Request) {
        // REQUEST
        request, err := decodeRequest(w, r, struct {
            Name     string `json:"name"`
            Email    string `json:"email"`
            Password string `json:"password"`
        }{})
        if err != nil {
            respondWithError(w, http.StatusBadRequest, "failed to decode request body")
            return
        }

        // CREATE USER
        hash, err := bcrypt.GenerateFromPassword([]byte(request.Password), 10)
        if err != nil {
            log.Printf("Error generating password hash: %s", err)
            w.WriteHeader(http.StatusInternalServerError)
            return
        }
        user, err := cfg.DB.CreateUser(r.Context(), database.CreateUserParams{
            ID:           uuid.New().String(),
            CreatedAt:    time.Now().UTC().Format(time.RFC3339),
            UpdatedAt:    time.Now().UTC().Format(time.RFC3339),
            Name:         request.Name,
            Email:        request.Email,
            Passwordhash: string(hash),
        })
        if err != nil {
            log.Printf("Error creating user: %s", err)
            respondWithError(w, http.StatusInternalServerError, "Couldn't create user")
            return
        }

        // RESPONSE
        respondWithJSON(w, http.StatusCreated, struct {
            ID        string `json:"id"`
            CreatedAt string `json:"created_at"`
            UpdatedAt string `json:"updated_at"`
            Name      string `json:"name"`
            Email     string `json:"email"`
        }{
            ID:        user.ID,
            CreatedAt: user.CreatedAt,
            UpdatedAt: user.UpdatedAt,
            Name:      user.Name,
            Email:     user.Email,
        })
    }

decodeRequest() and respondWithJSON() are helper functions defined elsewhere which decode the request into a Go struct and respond with a JSON body based on a Go Struct respectively. In this case, the main section of the handler function is responsible for actually creating the user based on the request. For postUser, it generates a hash from the provided password, then creates a database entry with the users data. Other handler functions follow a similar structure. 

#### Internal Packages

The api contains two internal package, 'auth' and 'database'. 

'auth' is used for authentication purposes. It has functions that:
  - Authenticate users by comparing passwords to saved password hash
  - Issue Access tokens to users so that they don't need to constantly send passwords (short duration, non-revocable)
  - Authenticates provided access tokens
  - Issue Refresh tokens to users so that they can obtain more access tokens (remember me functionality, long duration, revocable)
  - Authenticates provided refresh tokens and issues new access tokens
  - Revoke refresh tokens
  - Manage the generation of unique url-safe ids to be used for UID purposes

'database' is generated by SQLC. Queries are written in SQL in the ./sql/queries directory, and converted into the database package. 

#### Testing

I write tests for handlers before writing them, testing the expected functionality of the various endpoints. Tests can be seen in the main package with *_test.go format, executed using go test. The api is hosted at https://webnovelapi-y5hewbdc4a-nw.a.run.app (Seperate address to the client), so the endpoints can be tested independently to the client using Postman or other tools.

## Database Design and Management

The Database uses libsql, a fork of SQLite hosted by [Turso](https://turso.tech/), who I picked for their generous free plan since this is currently just a demonstration project. Migration is handled by goose, allowing me to migrate up and down between different schema. As mentioned previously, interaction via the database is handled with SQLC, where Go code is generated from SQL wirrten in the ./sql/queries directory.

## Frontend Development

The client codebase is organized within the ./client folder on GitHub. I created a react app, aiming to create a modern and responsive app that uses all the endpoints programmed in the API. I did not use any React Framework, since I wanted to use this opportunity to experiment with React and program these features myself instead of merely importing packages. 

The app displays a range of features, such as responsive design, dark/light modes, authentication contexts, and interactions with my API to fetch/post data. I recommend poking around the site to fully see what I've included [https://webnovelclient-y5hewbdc4a-nw.a.run.app/](https://webnovelclient-y5hewbdc4a-nw.a.run.app/).

## CI & CD

The project uses GitHub actions to constantly check my code. 

Continuous Integration (CI) is automated through GitHub Actions, which run on every pull request to the main branch. The process includes running tests (go test -cover) and performing security checks (gosec). Continuous Deployment (CD) is triggered upon successful CI completion, automatically deploying the latest builds to GCP.