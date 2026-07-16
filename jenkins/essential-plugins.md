## Jenkins Configuration Notes

### Stage View

- **Plugin Name:** [Pipeline: Stage Step](https://plugins.jenkins.io/pipeline-stage-step/)

### Role Based Work

- **Plugin Name:** [Role-based Authorization Strategy](https://plugins.jenkins.io/role-strategy/)  
    Security > Authorization > Role-Based Strategy

### Email Setup for SMTP

- **Plugin Name:** [Email Extension Plugin](https://plugins.jenkins.io/email-ext/)  
- **Plugin Name:** [Mailer Plugin](https://plugins.jenkins.io/mailer/)  
    System > Email Notification SMTP with PORT 465


### Tips for Shared Library Usage

- System > Global Trusted Pipeline Libraries
- Configure Pipeline: `@Library('name-of-the-library') _`
- How to Use Functions:

    ```pipeline
    steps {
        nameOfGroovyFunction(argIfAny)
    }
    ```
