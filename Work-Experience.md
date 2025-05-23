## 🌱 DevOps philosophy 

- How to **support developers**, to increase their productivity , by focusing only their tasks.
- How to **support to Organization**, to deliver the new features with out effecting existing features.
- Always **Automation** mind set.
- Early Feedback, Alerting
- Keep in mind, your pipelines **may not run by experts**, provide enough documentation.
- Platform & Tooling **Agnostic**ism
- Be Proactive, Not Reactive
- Embrace **Continuous Learning**
- Ready to adapt or change
- **Grab** the opportunity instead of waiting
  
## 🔁 DevOps and CI/CD experience

- Created **Docker** images for WMS/WLM applications with best practices.
  - Select the appropriate base image
  - Minimize the number of layers
  - Principle of least privilege.
  - Leverage build cache
  - Reduce the size of final image using multi-stage builds.
  - docker system prune to remove all dangling data (un-unsed Images).
  - use Semantic versioning for image tagging for roll back friendly deployments.
  - --no-cache builds for consistent and reliable image builds
  - <https://docs.google.com/presentation/d/15zxrsnx6XyJgjW4vwBWGRXxnbRVXt-xt/edit#slide=id.p1>
- Implemented comprehensive **Helm** charts including Pods, Deployments, Services, Ingress, and deployed applications into 
   the **AKS** cluster.
  - Created helm charts for Pods, deployments, services, Ingress
  - Implement various Container Design patterns like
      - Side car container
      - Init Container
      - Jobs, corn jobs
  - Liveness and Readiness probes are used to control the health of an application running inside Pod's container.
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
  - Idempotency
- Implemented various techniques to How to Improve the pipelines (**Scalability**) for larger work loads 
  - Infrastructure Scalability
    - Horizontal Scaling (Add more CI/CD servers or agents to handle additional load)
    - Dynamic agents using Docker Images.
  - Concurrent builds
    - Based on number of executors
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
  - Jenkins Hudson library with Maven
  - Implemented various [**JSL strategies**](Jenkins_Shared_Library_Designs.md).
- Designed and implemented JSL using Object-Oriented Programming (**OOPS**) concepts and Software Design Patterns, adhering to 
    **SOLID** principles for maintainability and scalability.
    - Function Over-loading for back ward compatibility
    - Single responsibility to reduce load time JSL
    - Dependency Inversion for loosely coupled 
- Developed and Contributed to the organization's shared library by implementing below methods,optimizing CI/CD automation
  - **Reusable** GitHub Composite Actions.
  - Reusable GitHub Workflows.
  - Jenkins Shared Libraries.
  - Python Reusable Libraries.
- Designed and implemented **agnostic**, script-driven CI/CD workflows to enhance scalability, flexibility, and 
  maintainability across Jenkins, GitHub Actions, minimizing migration efforts and operational overhead
- Designed and implemented **Sophisticated CI/CD** pipelines leveraging both **GitHub Actions** and **Jenkins**, integrated with **Python** automation.
  - Developed a pipeline to automatically update expired secrets across all environments 2000+, ensuring secure and efficient key rotation.
  - Used the Dynamic matrix stregy. Matrix is created and shared between work flows.
  - Cron,workflow_dispatch
- Subject Matter Expert (**SME**) in resolving technical **challenges** within CI/CD pipeline development.
  - As a senior number take the responsible of [**Technical challenges**](Technical_Challenges_in_Developing_Jenkins_CICDPipelines.md)
  - CPS issues resolved
- Implemented multiple strategies to address [**Flaky CI/CD builds**](https://docs.google.com/document/d/1eHpkg9evS8eRbtHxRXyRa_w1ODs_3MCG/edit?usp=drive_link&ouid=113894783804149609129&rtpof=true&sd=true).
  - Inconsistent Environments (dev, pre-prod,prod)
  - Firewall, Network issues
  - External API issues
     - Timeout issues
     - 4XX issues (Token/SPN Expiration)
     - 5xxx issues(re-try)
     - API rate issues
     - API change.
  - Agents might down
  - resource Limitations
    - IP Address not avialble
    - Subnet is full
    - Memory space
  - race conditions in pipelines
    - use Ansible play-book instead of Azure remote commands when share the same VM
- Skilled in deploying **Infrastructure as Code (IaC)** solutions using **Terraform** and [**Terragrunt**](https://terragrunt.gruntwork.io/), with a focus on precise version management for Terraform modules within a mono-repo.
  - Based on **DRY** DRY(donot repeat the your self) created Terrafom modules with combination of Terragrunt.
  - Implemented Terraform dependency management.
- **Owned** and managed **CI/CD infrastructure** for seamless delivery of production and non-production environments. Led **decommissioning** efforts to optimize resources and reduce costs.
  - Implemented Decommission pipelines which saves cost of Azure resources.
  - Added Dry-run option to the pipelines.
  - Added Over-ride params,more flexibility
- Ensured [**DevSecOps**](DevSecOps_Practices.md) enablement by securing pipelines from vulnerabilities.
  - Implemented integration of various SAST and DAST tools.
- Implemented Security and **secrets management** for Jenkins CI/CD and GitHub Actions work flows.
  - **Jenkins Pipelines**
    - Use Credential plugins
    - Use AKV
    - Folder Level Secrets
    - Global Level secrets
    - Use RBAC plugins
  - **GitHub Actions**
    - Using self-hosted runners based on Type of Env
    - Repo Level secrets
    - Organization Level secrets
    - Environment Level
    - Use Github environments
    - Use Github App
    - Use branch protection and repo rules
- Proficient in evaluating and selecting **DevOps tools** with a strong focus on **modernization** as a core mindset
  - Researched on DevOps tools like OpenTelementry , Jabera ..
  - [steps to evalute a tool](tool-evaluation-checklist.md)
- **Modernized** existing products through automation and containers (**SaaS transformation**).
- Implemented proactive Quality checks on customer environments using the Chef Inspec framework.
- Separation of environment config from code using Azure app config (**Twelve-factor** app principles).
- Acted as a **code owner** (via .CODEOWNERS) for shared repositories
  - Created pull request templates.
  - Add branch protection rules
  - Enforcing coding standards and security policies
  - Consistently reviewing and merging PRs
  - Maintaining project documentation
  - Integrating automated CI-checks using GitHub Actions and SonarQube
- Reduced manual efforts by automating **system tasks, builds, and deployments** using **Python** scripts integrated with **Jenkins** and **GitHub Actions**.
- **Proactively** engaged in the Code and PR reviews process, ensuring **coding standards** and **code quality.**
- Implemented [**Liquibase**](https://tinyurl.com/bdcs6mb2) for automated database schema versioning and integrated it with Jenkins CI/CD pipelines to 
   ensure seamless deployments, enforce database consistency, and enable rollback strategies across multiple environments.
- Actively participated in product design **Architecture meetings**, PI planning, and sprint backlog grooming.

## ⚒️ Builds and Automation experience

- "**Automation Mindset: Why Not Automate**?"
  - Proactively identify and eliminate manual tasks by implementing automation solutions for AppDynamics and Splunk 
    provisioning using Python and Ansible, improving efficiency, consistency, and scalability.
- Implemented **Build Performance**
  - Build Avoidance 
  - Incremental Builds
  - Caching
  - Dependency Analysis
  - Parallel Compilation
  - Distributed Builds
- Modernized ,Automated **legacy build processes**(Java with Make files), transitioning from Make to Maven, streamlining the builds.
  - Improved scalability/maintainability of codebase and easier debugging.
  - Handle native C components dll/.so files, 
  - Make them to CI/CD friendly builds.
- Contributed to Developing/fixing issues in Load Balancing, Service discovery and Directory services.
- Installed and configured the Linux servers with build specifications using Configuration Management tools.
- Designed and Developed Automation Regression Test Framework using JUNIT( Performance Optimization ).
- Deployed Microservices on GCP Kubernetes, ensuring scalability and reliability in high-scale systems.
- Implemented self-healing techniques and fault-tolerance services.
- Extensive experience with distributed build systems and build automation tools like Make and CMake, ensuring efficient 
  development processes and orchestration.
- Expert in memory layout optimization and proficient in implementing robust memory management techniques to prevent memory 
  leaks and enhance application stability.
- Proficient in the end-to-end C/C++ program development lifecycle, from Preprocessing and Compilation to Linking (Static 
  and Dynamic linking), Optimization, and cache-friendly code practices.
- Participated in product testing, verification, and validation processes to ensure high-quality deliverables.
- Demonstrated adaptability and flexibility in approaching complex challenges in mobile app development.
- Managed software dependency management system to ensure smooth and error-free builds and releases.

## ☁️ Cloud Experience

- Implemented [**AWS Well-Architected Framework principles**](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=desc) across multiple environments, improving system reliability, performance efficiency, and operational excellence
- Implemented various [**Cloud Design Patterns**](https://docs.google.com/document/d/1_QiESe2YJEmPy8qV-jd6Qx4cSImtFrn4/edit?usp=drive_link&ouid=113894783804149609129&rtpof=true&sd=true)
  - High Availability(replication,snapshot, multi az)
  - Processing Dynamic Content ( ELB, Auto Scaling )
  - Processing Static Content ( Cloud Front )
  - Uploading/Moving Data ( S3 )
  - Relational Databases( Read Replicas, Multi Az )
  - Batch Processing ( SQS )
  - Network ( Jump server, Private, public subnets )
  - Security
  - Cost Optimisation
- Orchestrated Subscription-Based Multi-Tenant Products on Diverse Public Cloud Service Providers.
- Designed and Developed Enhancements of CSG using AWS APIS.
- Enhanced the existing product with features like User roles ( Lead, System Administration, Developer ), ELB, Autoscaling, 
  SES, SQS, and RDS scheduling, S3 backup policies improving overall system resiliency at scale.
- Created monitors, alarms, and notifications for EC2 hosts using Cloud Watch, Cloud Trail, and SNS.
- Played a pivotal role in cloud security, VPC, VPN, IAM management, networking protocols and cost optimization.
- Developed AWS CloudFormation templates for VPC and subnets, streamlining infrastructure provisioning.
- Migrated on-premises production applications to the hybrid AWS environment, aligning with strategic goals.
- Worked with various SaaS( Software as a Service ), IaaS and PaaS.
- Involved in Disaster Recovery and fail-over strategies, minimizing downtime and ensuring business continuity.

## 🔭 Observability and Monitoring 

- Integrating **OpenTelemetry** with Jenkins Pipelines, along with Elasticsearch and Jaeger, is an excellent approach for 
  distributed tracing, performance monitoring, and debugging latency issues.  
- Established K8's cluster **observability** with Elasticsearch, Prometheus, Grafana, Azure Monitor, and ELK Stack.
- Implemented AppDynamics to monitor and optimize database performance, including SQL queries, transaction times, and health 
  metrics.
- Integrated Splunk for centralized log aggregation and monitoring, enhancing observability of application metrics, error 
  rates, and user transactions.

## 🔧 On-Call SRE Support & Incident Management

- Provided on-call SRE support to promptly resolve critical production issues and reduce downtime.
  -  USE method to detect potential issues before they impact users, improving system
- Led and coordinated **bridge calls** during high-severity incidents to ensure fast recovery and clear communication.
- Documented incident handling processes, troubleshooting steps, and recovery actions for future reference.
- Created and shared detailed **postmortem reports**, capturing root cause, impact, timeline, and actionable follow-ups.
- Implemented proactive monitoring and alerting to catch issues early and reduce alert fatigue.
- Collaborated cross-functionally with DB Team, infra, Network teams to triage the issue.
- Contributed to incident **runbooks** and knowledge base articles to support future **on-call rotations**.

## 🤝 Leadership & Collaboration

- **Mentored** and trained junior team members, fostering a culture of continuous learning and growth.
  - Prepared onboarding material (Confluence pages,tools and requried software)
  - Conducted hands-on workshops
  - Assigned initial Jira tickets with low complexity   
- Collaborated with **cross-functional teams** to identify and triage issues, ensuring timely problem resolution.
  - Collaborated with various cross functional teams like DB team, network Team and Developer Team and onboard Teams
- Actively helps ramp up the team during the **hiring process** by sharing context, **onboarding**, and **training support**.
- Helps teammates see how their work fits into the bigger picture.
- Tracks personal work progress and checks it against what was planned.
- Led and inspired the team through coaching, mentorship, and analytical skills with a touch of humor.
- Uses product knowledge to spot risks early and keep things moving in the right direction.
- **Triage Team** Contributions
  - Actively participated in the triage process, especially during high-volume periods.
  - Investigated issues by analyzing logs and reviewing existing code
  - Categorized findings into actionable items by converting them into Jira defects or stories as appropriate. 

## 🎨🛠️ Design & Developer Experience

- Implemented **Object-Oriented Programming (OOP)** principles across multiple languages — **Java**, **Groovy**, and **Python** — to write clean, modular, and maintainable components.
  - Compile-time polymorphism
  - Run-time Polymorphism
  - Abstraction
  - Encapsulation
- Applied key **Design Patterns** in real-world projects, including:
  - Creational ( Singleton, Factory )
  - Structural (Builder, Adapter)
  - Behavioral ( Observer, Chain of Responsibility )
- Advocate for **SOLID Principles** to promote scalable, testable, and robust architecture:
  - **S**ingle Responsibility --> Reduce JSL load time
  - **O**pen/Closed  --> seamless addition of features
  - **L**iskov Substitution  
  - **I**nterface Segregation  --> Created fine-grained interfaces, Jenkins Global Var
  - **D**ependency Inversion --> Loosely coupled components
- Applied **Twelve-Factor App** principles to streamline application delivery using JSL, Jenkins, and GitHub Actions
  - Code base ( Mono repo and Multi Repo )
  - Separation App config using Azure app config
  - Dependency isolation using Python requirements.txt, VPython
  - logs as event streams using Opentelemetry, Splunk ..etc
  - Build, Release
- Experience writing **unit tests and integration tests**, emphasizing TDD/BDD practices.
  - pytest ( Fixtures, Parametrized Tests, pytest-xdist for parallel )
  - JUnit
  - Mocking
  - Test coverage ( Coverage.py, JaCoCo, SonarQube )
  - jenkinspipelineTest
- Built developer-first internal tools with reusability, extensibility, and clear documentation in mind.

## 🤖 AI-Augmented Developer Workflow (Vibe Coding Mode 🔥)

- Harnessing the power of AI tools to supercharge software development with efficiency, clarity, and precision.
- Researched and crafted appropriate **prompts** to speed up code development, including refactoring, adding unit test cases, 
  and improving documentation.
- Used **GitHub Copilot** to assist with:
  - Pull Request (PR) Reviews
  - Generate Documentation
  - Code Refactoring
  - Code Formatting
  - Test Case Generation
- Integrated **Dependabot** to manage dependencies proactively:
  - Performed **automated version upgrades**.
  - Mitigated known vulnerabilities and kept libraries up to date.
- Explored **MLOps concepts** (AI and Machine Learning Operations).
