<a name="readme-top"></a>


[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://kafka.apache.org/">
    <img src="https://kafka.apache.org/logos/kafka_logo--simple.png" alt="Logo" width="400" height="">
  </a>

  <h3 align="center">Keycloak</h3>

  <p align="center">
  Apache Kafka is an open-source distributed event streaming platform used by thousands of companies for high-performance data pipelines, streaming analytics, data integration, and mission-critical applications.
    <br />
    <a href="https://kafka.apache.org/documentation/"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="http://20.64.115.37:8090/auth">View Demo</a>
    ·
    <a href="https://github.com/Great-Side-Projects/kafka/issues">Report Bug</a>
    ·
    <a href="https://github.com/Great-Side-Projects/kafka/issues/new">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
        <li><a href="#Architecture-design">Architecture design</a></li>
        <li><a href="#Architecture-diagram">Architecture diagram</a></li>
     </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot-UI]](https://authsp.azurewebsites.net/)
[![Product Name Screen Shot2][product-screenshot-UI2]](https://authsp.azurewebsites.net/)
I am using Kafka to my side projects to improve the arquitecture od software. Kafka deployment with docker-compose SASL and KAfka UI authentication, this project is how to deploy a Kafka cluster with SASL authentication and Kafka UI with docker-compose in a VM Azure or local environment.   

<p align="right">(<a href="#readme-top">back to top</a>)</p>


### Built With

This project is built with the following technologies:


* [![Docker][DockerImage]](https://www.docker.com/)
* [![VM][AzureVM]](https://azure.microsoft.com/es-es/services/virtual-machines/)


### Architecture design

The architecture design is based in how to deploy kafka cluster in a VM Azure with  CI/CD in GitHub Actions.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Architecture diagram
[![Architecture diagram][architecture-diagram]](http://20.64.115.37:8090/auth)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

Here you can find the steps to run the project in your local environment to explore the Kafka proyect.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.

* Docker
* Docker-compose
* Zookeeper
* Kafka UI
* if you are in a VM, you need to open the port 8090 and 9092 a public access to the kafka server. 

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/Great-Side-Projects/kafka.git
   ```
2. Go to the root folder of the project
   ```sh
   cd kafka
   ``` 
3. find a docker file "Kafaka-compose-local" and set the environment variables in the dockercompose. root folder of the project. visit the documentation of the Kafka, zookeeper and Kafka UI to set the environment variables. 
- https://hub.docker.com/r/bitnami/kafka 
- https://hub.docker.com/r/bitnami/zookeeper 
- https://hub.docker.com/r/provectuslabs/kafka-ui 
- https://docs.kafka-ui.provectus.io/

   ```yaml
   kafka:
     environment:
       KAFKA_CLIENT_USERS: app1 #user for the kafka client, Separated by commas, semicolons or whitespaces. 
       KAFKA_CLIENT_PASSWORDS: app1pass #password for the kafka client, Separated by commas, semicolons or whitespaces.
   kafka-ui:
     enviroment:
      SPRING_SECURITY_USER_NAME: admin #user for the kafka ui
      SPRING_SECURITY_USER_PASSWORD: admin #password for the kafka ui
   ```

4. Create the docker-compose with the following command
 
   ```sh
    docker compose -f kafka-compose-local.yaml up
    ctrl + c to stop the docker-compose
   ```
5. Open your browser and go to `http://localhost:8090/` to see the UI kafka login.
6. Login with the user and password that you have configured in the docker-compose file. explore de UI and the kafka cluster from console. 
    ```yaml
    kafka-ui:
      environment:
        SPRING_SECURITY_USER_NAME: admin #user for the kafka ui
        SPRING_SECURITY_USER_PASSWORD: admin #password for the kafka ui
    ```
8. if you want to authenticate you client to kafka cluster with SASL, you have set the configuration in the client java, .net or python.  
    ```yaml
    kafka:
      bootstrap-servers: localhost:9092
      properties:
        sasl.mechanism: PLAIN
        sasl.jaas.config: org.apache.kafka.common.security.plain.PlainLoginModule required username='app1' password='app1pass';
      security:
        protocol: SASL_PLAINTEXT #SASL_SSL or PLAINTEXT
    ```
7. Enjoy!

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

### Easy way:
Go to `http://localhost:8090/` and you can see the UI to manage the kafka.


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ROADMAP -->
## Roadmap

- [x] Implement Docker compose for deployment
- [x] Implement CI/CD with GitHub Actions
- [x] Implement VM Azure for deployment
- [ ] Implement SSO with Keycloak

See the [open issues](https://github.com/Great-Side-Projects/kafka/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the "develop" Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Angel Morales - [LinkedIn](https://www.linkedin.com/in/angelmoralesb/) - angelmoralesb@gmail.com

Project Link: [https://github.com/Great-Side-Projects/kafka](https://github.com/Great-Side-Projects/keycloak)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [kafka](https://kafka.apache.org/)
* [Choose an Open Source License](https://choosealicense.com)
* [Docker](https://www.docker.com/)
* [GitHub Actions](https://docs.github.com/es/actions)
* [Kafka UI](https://docs.kafka-ui.provectus.io/)
* [Kafka UI Docker](https://hub.docker.com/r/provectuslabs/kafka-ui)
* [Zookeeper Docker](https://hub.docker.com/r/bitnami/zookeeper)
* [Kafka Docker](https://hub.docker.com/r/bitnami/kafka)

 
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/Great-Side-Projects/kafka/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/Great-Side-Projects/kafka/forks
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/Great-Side-Projects/kafka/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/
[issues-url]: https://github.com/Great-Side-Projects/kafka/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/Great-Side-Projects/quickshortapi/blob/main/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/angelmoralesb/
[product-screenshot-UI]: images/screenshotUI.png
[DockerImage]: https://img.shields.io/badge/Docker-0db7ed?style=for-the-badge&logo=docker&logoColor=white
[AzureWebApp]: https://img.shields.io/badge/Azure%20Web%20App-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white
[PostgreSQL]: https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white
[architecture-diagram]: images/kafka-Architecture-Design.drawio.png
[AzureVM]: https://img.shields.io/badge/Azure%20VM-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white
[product-screenshot-UI2]: images/screenshotUI2.png




















