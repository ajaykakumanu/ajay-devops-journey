## DevOps and CI/CD experience

- Created **Docker** images for WMS/WLM applications with best practices.
  - Select the appropriate base image
  - Minimize the number of layers
  - Principle of least privilege.
  - Leverage build cache
  - Reduce the size of final image using multi-stage builds.
  - <https://docs.google.com/presentation/d/15zxrsnx6XyJgjW4vwBWGRXxnbRVXt-xt/edit#slide=id.p1>
- Implemented comprehensive **Helm** charts including Pods, Deployments, Services, Ingress, and deployed applications into 
   the **AKS** cluster.
  - Created helm charts for Pods, deployments, services, Ingress
  - Implement various Container Design patterns like Side car container, Init Container, Jobs, corn jobs.
  - Liveness and Readiness probes are used to control the health of an application running inside Pods ‘container.
  - Used ConfigMap and Secrets to store non-confidential data in Key value pair.
  - Implemented Kubernetes [**Security best practices**](Kubernetes_Best_Practices.md)
- Implemented various types of **CI/CD pipeline patterns**
  - Applications deployment pipeline.
  - Infrastructure as a pipe line code.
  - Builds Once deploy many times.
  - Trigger the Right Pipeline like a chain fashion.
  - Run parallel.
- Implemented following reliability strategies **CI/CD pipeline patterns** to enhance delivery efficiency, fault tolerance, 
     and high availability during deployments. [**Reliability patterns**](Reliability_Patterns_Applied_in_CICD.md)
  - Circuit Breaker
  - Bulkhead
  - Timeout
  - Fail-back
- Implemented various techniques to How to Improve the pipelines (**Scalability**) for larger work loads 
  - Infrastructure Scalability
    - Horizontal Scaling (Add more CI/CD servers or agents to handle additional load)
    - Dynamic agents using Docker Images.
  - Parallelism in Builds
    - Configure pipelines to run multiple jobs in parallel. (Ex: matrix stretegy )
    - Configure pipelines to run multiple satges in parallel (Ex : use parallel)
  - Customize builds based on Environment and skip few stages
    - Dev, Non prod does not need all stages.
  - Using multi-agent Jenkins based on the region
    - Reduce the latency issues if Jenkins agent and deployble VM is same region
  - Added notification, if any build failure
     - Get the quicker feed back
  - Added best practices about JSL
  - Try to use Declarative than Scripted
  - Monitoring and Logging
    - Use observebility tool like telemetry to troubleshoot issues.
  - Pipeline Optimization
    - Caching (Implement caching mechanisms to reuse dependencies and artifacts between builds)
    - Incremental Builds (Configure the pipeline to only build and test changed components rather than the entire project)
- Developed Jenkins **Custom** plug-ins (Build Failure Analysis plugin) and Jenkins Shared Libraries (JSL) strategies.
  - Implemented various [**JSL strategies**](Jenkins_Shared_Library_Designs.md).
  - Designed and implemented JSL using Object-Oriented Programming (OOP) concepts and Software Design Patterns, adhering to 
    SOLID principles for maintainability and scalability.
- Developed and contributed to the organization's shared library by implementing **reusable GitHub workflows** and Jenkins 
  shared libraries, optimizing CI/CD automation and standardizing pipeline processes across teams
- Designed and implemented **agnostic**, script-driven CI/CD workflows to enhance scalability, flexibility, and 
  maintainability across Jenkins, GitHub Actions, minimizing migration efforts and operational overhead
- Subject Matter Expert (**SME**) in resolving technical **challenges** within CI/CD pipeline development.
  - As a senior number take the responsible of [**Technical challenges**](Technical_Challenges_in_Developing_Jenkins_CICDPipelines.md)
  - CPS issues resolved
- Skilled in deploying **Infrastructure as Code (IaC)** solutions using Terraform and Terragrunt, with a focus on precise version management for Terraform modules within a mono-repo.
  - Based on DRY DRY(donot repeat the your self) created Terrafom modules.
  - Implement Terraform dependency management.
- **Owned** and managed **CI/CD infrastructure** for seamless delivery of production and non-production environments. Led decommissioning efforts to optimize resources and reduce costs.
  - Implemented Decommission pipelines which saves cost of Azure resources.
- Ensured [**DevSecOps**](DevSecOps_Practices.md) enablement by securing pipelines from vulnerabilities.
  - Implemented integration of various SAST and DAST tools.
- Proficient in evaluating and selecting **DevOps tools** with a strong focus on **modernization** as a core mindset
  - Researched on DevOps tools like OpenTelementry , Jabera ..
- **Modernized** existing products through automation and containers (**SaaS transformation**).
- Collaborated with **cross-functional teams** to identify and triage issues, ensuring timely problem resolution.
  - Collaborated with various cross functional teams like DB team, network Team and Developer Team and onboard Teams
- Implemented proactive Quality checks on customer environments using the Chef Inspec framework.
- Separation of environment config from code using Azure app config (**Twelve-factor** app principles).
- Reduced manual efforts by automating **system tasks, builds, and deployments** using **Python** scripts integrated with **Jenkins** and **GitHub Actions**.
- **Proactively** engaged in the Code and PR reviews process, ensuring **coding standards** and **code quality.**
- **Mentored** and trained junior team members, fostering a culture of continuous learning and growth.
- Implemented [**Liquibase**](https://tinyurl.com/bdcs6mb2) for automated database schema versioning and integrated it with Jenkins CI/CD pipelines to 
   ensure seamless deployments, enforce database consistency, and enable rollback strategies across multiple environments.
- Actively participated in product design **Architecture meetings**, PI planning, and sprint backlog grooming.
- Provided on-call SRE support, promptly resolving critical issues and ensuring system stability.
- Utilized **AI tools** like GitHub Copilot and Dependabot to accelerate delivery and dependency management.
  - Researched and crafted appropriate **prompts** to speed up code development, including refactoring, adding unit test cases, 
    and improving documentation.
  - Implemented GitHub Copilot for pull request (PR) reviews to enhance code quality.
  - Used Dependabot to identify the latest versions of dependencies, apply patches, and mitigate security vulnerabilities.
- Explored **MLOps concepts** (AI and Machine Learning Operations).

## Builds and Automation experience

- "**Automation Mindset: Why Not Automate**?"
  - Proactively identify and eliminate manual tasks by implementing automation solutions for AppDynamics and Splunk 
    provisioning using Python and Ansible, improving efficiency, consistency, and scalability.
- Designed and delivered "single-click" deployment solutions (canary).
- Modernized ,Automated legacy build processes, transitioning from Make to Maven, streamlining the builds.
- Contributed to Developing/fixing issues in Load Balancing, Service discovery and Directory services.
- Installed and configured the Linux servers with build specifications using Configuration Management tools.
- Designed and Developed Automation Regression Test Framework( Performance Optimization ).
- Deployed Microservices on GCP Kubernetes, ensuring scalability and reliability in high-scale systems.
- Implemented self-healing techniques and fault-tolerance services.
- Proficiently led Root cause analysis(RCA) for incidents through the utilization of incident post-mortems to accurately 
  diagnose and resolve issues.
- Extensive experience with distributed build systems and build automation tools like Make and CMake, ensuring efficient 
  development processes and orchestration.
- Expert in memory layout optimization and proficient in implementing robust memory management techniques to prevent memory 
  leaks and enhance application stability.
- Proficient in the end-to-end C/C++ program development lifecycle, from Preprocessing and Compilation to Linking (Static 
  and Dynamic linking), Optimization, and cache-friendly code practices.
- Participated in product testing, verification, and validation processes to ensure high-quality deliverables.
- Demonstrated adaptability and flexibility in approaching complex challenges in mobile app development.
- Managed software dependency management system to ensure smooth and error-free builds and releases.

## Cloud Experience

- Orchestrated Subscription-Based Multi-Tenant Products on Diverse Public Cloud Service Providers.
- Designed and Developed Enhancements of CSG using AWS APIS.
- Enhanced the existing product with features like User roles (Lead, System Administration, Developer), ELB, Autoscaling, 
  SES, SQS, and RDS scheduling, S3 backup policies improving overall system resiliency at scale.
- Created monitors, alarms, and notifications for EC2 hosts using Cloud Watch, Cloud Trail, and SNS.
- Played a pivotal role in cloud security, VPC, VPN, IAM management, networking protocols and cost optimization.
- Developed AWS CloudFormation templates for VPC and subnets, streamlining infrastructure provisioning.
- Migrated on-premises production applications to the hybrid AWS environment, aligning with strategic goals.
- Led and inspired the team through coaching, mentorship, and ramping up, demonstrating strong leadership, teamwork, and 
  analytical skills with a touch of humor.
- Worked with various SaaS(Software as a Service), IaaS and PaaS.
- Involved in Disaster Recovery and fail-over strategies, minimizing downtime and ensuring business continuity.

## Observability and Monitoring 

- Integrating **OpenTelemetry** with Jenkins Pipelines, along with Elasticsearch and Jaeger, is an excellent approach for 
  distributed tracing, performance monitoring, and debugging latency issues.  
- Established K8's cluster **observability** with Elasticsearch, Prometheus, Grafana, Azure Monitor, and ELK Stack.
- Implemented AppDynamics to monitor and optimize database performance, including SQL queries, transaction times, and health 
  metrics.
- Integrated Splunk for centralized log aggregation and monitoring, enhancing observability of application metrics, error 
  rates, and user transactions.
