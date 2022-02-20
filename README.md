# Continuous integration workflow
The goal of this project is to develop a continuous integration workflow.
This workflow is based on a micro-service architecture, it is fully containerized using Docker. It contains a continuous integration server (Jenkins), a source code management solution (GitLab), a Docker private registry and differents monitoring tools. Real-time metrics solutions are used before and after deployment.
The workflow can be used to manage different types of applications. The Jenkins server is responsible for deploying the different environments (dev, prod, etc.), it launches the unit and functional tests, then sends and stores the results of these tests.
The configuration is fully editable through the Jenkinsfiles and Dockerfiles. To add a tool, you just have to modify the dockerfile, to modify the continuous integration pipeline of a project, you just have to modify the Jenkinsfile it contains.

## Launch the tools
```
    docker-compose up
```

### Metrics collected before application deployment 
- Sonarqube:
The SonarQube tool is used to collect information on the code quality of applications before deployment.

### Metrics collected after application deployment 
- cAdvisor:
Exposes the metrics of Docker containers running on the server.
- node exporter:
Exposes server metrics.
- Prometheus:
Scans the different targets at a set interval to collect the metrcis.
- Prometheus metrics plugin installed in Jenkins:
Exposes a specific access point to allow Prometheus to collect metrics about the Jenkins CI solution.
- Grafana:
Displays as dashboards the metrcis stored by the defined data source (here Prometheus)