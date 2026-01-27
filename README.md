# 🚀 7-Day DevOps Challenge: CI/CD Pipeline with AWS

![CI/CD Pipeline](https://img.shields.io/badge/AWS-CI%2FCD%20Pipeline-orange?style=for-the-badge&logo=amazon-aws)
![Java](https://img.shields.io/badge/Java-Application-red?style=for-the-badge&logo=openjdk)
![DevOps](https://img.shields.io/badge/DevOps-Challenge-blue?style=for-the-badge)

A comprehensive hands-on DevOps project building a complete CI/CD pipeline from scratch using AWS services and Java. This 7-day challenge demonstrates modern DevOps practices, automated deployment workflows, and cloud infrastructure management.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Day-by-Day Breakdown](#day-by-day-breakdown)
- [Getting Started](#getting-started)
- [Key Learnings](#key-learnings)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Pipeline Flow](#pipeline-flow)
- [Troubleshooting](#troubleshooting)
- [Author](#author)

---

## 🎯 Overview

This project implements a fully automated CI/CD pipeline that takes Java code from commit to production deployment. The deployment pipeline built in this project is invisible to the end-user, but makes a significant impact by automating the entire software release process—from code commit to live deployment.

By completing this challenge, I've gained practical experience in:

- **Continuous Integration (CI)**: Automatically building and testing code changes
- **Continuous Deployment (CD)**: Automatically deploying tested code to production
- **Infrastructure as Code (IaC)**: Managing cloud resources programmatically
- **DevOps Best Practices**: Bridging the gap between development and operations
- **Cloud-Native Development**: Building and deploying applications entirely on AWS infrastructure

---

## 🏗️ Architecture

![Project Architecture](https://learn.nextwork.org/projects/static/aws-devops-cicd/aws-cicd.png)



**Pipeline Components:**

1. **Development Environment**: EC2 instances with Visual Studio Code for remote cloud development
2. **GitHub**: Version control and source code repository
3. **CodeArtifact**: Dependency management and artifact storage
4. **CodeBuild**: Automated build and testing service
5. **S3 Bucket**: Storage for build artifacts
6. **CodeDeploy**: Automated deployment to EC2 instances
7. **CodePipeline**: Orchestrates the entire CI/CD workflow
8. **Web Server**: EC2 instance hosting the live Java application

> **Note**: All development and deployment happens entirely on AWS cloud infrastructure, enabling seamless integration and scalability.

---

## 💻 Technologies Used

### AWS Services
- **AWS Cloud9** - Cloud-based IDE
- **AWS CodeArtifact** - Artifact repository manager
- **AWS CodeBuild** - Continuous integration service
- **AWS CodeDeploy** - Automated deployment service
- **AWS CodePipeline** - Continuous delivery orchestration
- **Amazon S3** - Object storage for artifacts
- **Amazon EC2** - Virtual servers for hosting
- **AWS CloudFormation** - Infrastructure as Code
- **AWS IAM** - Identity and access management

### Development Stack
- **Java** - Primary programming language
- **Maven** - Build automation and dependency management
- **Visual Studio Code** - Cloud IDE connected to EC2 instances for remote development
- **Git/GitHub** - Version control
- **YAML** - Configuration files

---

## 📁 Project Structure

```
devops-challenge-java/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── devopschallenge/
│   │   │           └── webapp/
│   │   │               ├── Application.java
│   │   │               └── controller/
│   │   │                   └── HomeController.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── static/
│   │           └── index.html
│   └── test/
│       └── java/
│           └── com/
│               └── devopschallenge/
│                   └── webapp/
│                       └── ApplicationTests.java
├── buildspec.yml
├── appspec.yml
├── scripts/
│   ├── install_dependencies.sh
│   ├── start_server.sh
│   └── stop_server.sh
├── cloudformation/
│   └── infrastructure.yml
├── pom.xml
└── README.md
```

---

## 📅 Day-by-Day Breakdown

### Day 1️⃣: Set Up a Web App in the Cloud
**Objective**: Create a Java web application in a cloud-based development environment

**What I Built**:
- Configured AWS EC2 instances for cloud development
- Connected Visual Studio Code to EC2 for remote development
- Created a Spring Boot Java web application
- Set up the project structure and dependencies
- Tested the application locally on the cloud instance

**Skills Gained**: Cloud IDE setup, VS Code remote development, Java Spring Boot basics, AWS EC2 management

---

### Day 2️⃣: Connect a GitHub Repo with AWS
**Objective**: Set up version control and integrate with AWS

**What I Built**:
- Created a GitHub repository for the project
- Configured Git in the cloud development environment
- Connected AWS services to GitHub using OAuth authentication
- Set up webhooks for automated pipeline triggers

**Skills Gained**: Git version control, GitHub integration, AWS-GitHub connectivity, OAuth configuration

---

### Day 3️⃣: Store Dependencies in CodeArtifact
**Objective**: Implement centralized dependency management

**What I Built**:
- Created a CodeArtifact repository
- Configured Maven to use CodeArtifact
- Set up authentication and domain
- Published and retrieved Java packages

**Skills Gained**: Artifact management, Maven configuration, dependency security

---

### Day 4️⃣: Package an App with CodeBuild
**Objective**: Automate the build process using CI principles

**What I Built**:
- Created a CodeBuild project
- Wrote buildspec.yml for build instructions
- Configured build environment for Java/Maven
- Implemented automated testing in the pipeline

**Skills Gained**: Continuous Integration, build automation, buildspec configuration

**buildspec.yml highlights**:
```yaml
version: 0.2
phases:
  install:
    runtime-versions:
      java: corretto11
  build:
    commands:
      - mvn clean install
artifacts:
  files:
    - target/*.jar
```

---

### Day 5️⃣: Deploy an App with CodeDeploy
**Objective**: Automate application deployment to EC2

**What I Built**:
- Created CodeDeploy application and deployment group
- Configured EC2 instances with CodeDeploy agent
- Wrote appspec.yml for deployment instructions
- Created deployment lifecycle scripts

**Skills Gained**: Continuous Deployment, EC2 management, deployment automation

**appspec.yml highlights**:
```yaml
version: 0.0
os: linux
files:
  - source: /
    destination: /home/ec2-user/app
hooks:
  ApplicationStop:
    - location: scripts/stop_server.sh
  ApplicationStart:
    - location: scripts/start_server.sh
```

---

### Day 6️⃣: Automate Infrastructure with CloudFormation ⭐ (Bonus)
**Objective**: Implement Infrastructure as Code

**What I Built**:
- Created CloudFormation templates in YAML
- Defined EC2 instances, security groups, and IAM roles
- Implemented stack creation and updates
- Practiced infrastructure versioning

**Skills Gained**: Infrastructure as Code, CloudFormation, resource management

---

### Day 7️⃣: CI/CD with CodePipeline
**Objective**: Orchestrate the complete CI/CD pipeline

**What I Built**:
- Created a CodePipeline connecting all services
- Configured stages: Source → Build → Deploy
- Set up automated triggers on code commits
- Implemented pipeline monitoring and notifications

**Skills Gained**: Pipeline orchestration, end-to-end automation, DevOps workflow

**Pipeline Stages**:
1. **Source**: Detects changes in GitHub repository
2. **Build**: CodeBuild compiles Java code and runs tests
3. **Deploy**: CodeDeploy pushes application to EC2 instances

---

## 🚀 Getting Started

### Prerequisites

- AWS Account ([Sign up here](https://aws.amazon.com/))
- GitHub Account
- Basic understanding of Java
- Familiarity with command line

### Setup Instructions

#### 1. Clone the Repository
```bash
git clone https://github.com/YOUHAD08/aws-cicd-pipeline.git
cd aws-cicd-pipeline
```

#### 2. Install Dependencies
```bash
mvn install
```

#### 3. Set Up AWS Resources
```bash
# Configure AWS CLI
aws configure

# Create S3 bucket for artifacts
aws s3 mb s3://your-devops-challenge-bucket

# Create CodeArtifact repository
aws codeartifact create-repository \
    --domain my-domain \
    --repository my-repo
```

#### 4. Configure Maven Settings
Update `~/.m2/settings.xml` with CodeArtifact authentication:
```xml
<settings>
  <servers>
    <server>
      <id>codeartifact</id>
      <username>aws</username>
      <password>${env.CODEARTIFACT_AUTH_TOKEN}</password>
    </server>
  </servers>
</settings>
```

#### 5. Build the Application Locally
```bash
# Clean and build
mvn clean package

# Run tests
mvn test

# Start the application
java -jar target/webapp-1.0.0.jar
```

#### 6. Deploy the Pipeline
```bash
# Create CloudFormation stack
aws cloudformation create-stack \
    --stack-name devops-challenge-stack \
    --template-body file://cloudformation/infrastructure.yml \
    --capabilities CAPABILITY_IAM
```

---

## 🔄 Pipeline Flow

![Pipeline Flow](./Pipeline%20Flow.png)

**Average Pipeline Execution Time**: ~5-8 minutes

---

## 🎓 Key Learnings

### DevOps Principles
- **Automation First**: Reducing manual intervention minimizes errors and speeds delivery
- **Infrastructure as Code**: Treating infrastructure configuration as code enables version control and reproducibility
- **Continuous Feedback**: Automated testing provides immediate feedback on code quality

### CI/CD Benefits
- **Faster Time to Market**: Automated pipelines reduce deployment time from days to minutes
- **Reduced Risk**: Small, frequent deployments are easier to troubleshoot than large releases
- **Improved Collaboration**: Clear pipeline stages help dev and ops teams work together

### AWS Best Practices
- **Least Privilege Access**: Using IAM roles with minimal necessary permissions
- **Resource Tagging**: Organizing resources for cost tracking and management
- **Monitoring**: Setting up CloudWatch for pipeline and application monitoring

---

## 🔧 Troubleshooting

### Common Issues

**Issue**: CodeBuild fails with "Access Denied" error
```bash
Solution: Check IAM role permissions for CodeBuild service role
- Ensure S3 bucket policies allow CodeBuild access
- Verify CodeArtifact authentication token is valid
```

**Issue**: CodeDeploy agent not running on EC2
```bash
Solution: SSH into EC2 and restart the agent
sudo service codedeploy-agent restart
sudo service codedeploy-agent status
```

**Issue**: Maven build fails to download dependencies
```bash
Solution: Verify CodeArtifact configuration
- Check ~/.m2/settings.xml configuration
- Regenerate CodeArtifact auth token
- Verify network connectivity from build environment
```

**Issue**: Application not accessible after deployment
```bash
Solution: Check security group rules
- Ensure port 8080 (or your app port) is open
- Verify EC2 instance is running
- Check application logs: /var/log/webapp.log
```

---

## 📚 Resources

- [AWS DevOps Documentation](https://aws.amazon.com/devops/)
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Maven Documentation](https://maven.apache.org/guides/)
- [Git Best Practices](https://git-scm.com/book/en/v2)

---

## 🏆 Achievements

✅ Built a complete CI/CD pipeline from scratch  
✅ Automated build, test, and deployment processes  
✅ Implemented Infrastructure as Code with CloudFormation  
✅ Gained hands-on experience with 7 AWS services  
✅ Created production-ready DevOps documentation  
✅ Demonstrated modern DevOps best practices  

---

## 👨‍💻 Author

**YOUHAD AYOUB**

- Completed: January 2026
- Challenge: 7-Day DevOps Challenge
- Platform: NextWork

---

## 📝 License

This project is part of the NextWork 7-Day DevOps Challenge and is intended for educational purposes.

---

## 🤝 Acknowledgments

- **[NextWork](https://learn.nextwork.org/app)** for providing the structured learning path and project guide. [Get started with this DevOps series project by clicking here](https://learn.nextwork.org/projects/aws-devops-cicd)
- AWS for comprehensive documentation and free tier resources
- The DevOps community for best practices and guidance

---

## 📞 Connect

**YOUHAD AYOUB**  
📧 Email: [yo_ayoub@etu.enset-media.ac.ma](mailto:yo_ayoub@etu.enset-media.ac.ma)  
💼 LinkedIn: [Connect with me](https://www.linkedin.com/in/youhad-ayoub/)  
🐙 GitHub: [@YOUHAD08](https://github.com/YOUHAD08)

Have questions or want to collaborate on DevOps projects? Feel free to reach out!


---

## 💭 Project Status & Future Development

This CI/CD pipeline continues to evolve as I apply my DevOps learnings to future projects. The infrastructure is designed to be scalable and maintainable, demonstrating production-ready DevOps practices.

Thank you for exploring this project! I'll continue to build and enhance this pipeline as I gain more experience in cloud infrastructure and DevOps automation.

---

**Built with ☕ and determination during the 7-Day DevOps Challenge**