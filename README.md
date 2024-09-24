# CI-CD-Pipeline-Configuration-Manager-YAML

Simplify and automate the setup of CI/CD pipelines using GitHub Actions
Allows you to define build, test, and deploy stages using a single YAML configuration file, making it easy to replicate and manage pipelines across multiple projects.

## Features
✨ YAML-based Configuration: Define your CI/CD pipeline stages (build, test, deploy) in a simple YAML file. <br>
✨ Automated Workflow Generation: Automatically generates GitHub Actions workflow files based on your configuration. <br>
✨ Supports Multiple Environments: Easily configure pipelines for different environments (development, staging, production). <br>
✨ Flexible Customization: Customize build steps, testing commands, and deployment procedures. <br>



## How to Use

Prerequisites
- Python 3.x
- PyYAML library: Install it using `pip install pyyaml`
- GitHub repository with GitHub Actions enabled
- Clone repository:  `git clone https://github.com/your-username/cicd-pipeline-config-manager.git`
- Move to directory: `cd cicd-pipeline-config-manager`
- Install required Python packages: `pip install -r requirements.txt`


### Step 1 Create a YAML configuration file named pipeline.yaml in the root of your project

```
pipeline:
  build:
    - name: Install Dependencies
      run: npm install
  test:
    - name: Run Unit Tests
      run: npm test
  deploy:
    - name: Deploy to Production
      if: github.ref == 'refs/heads/main'
      run: ./deploy.sh production
```

### Step 2 Run the script to generate the GitHub Actions workflow file:

```
python generate_workflow.py
```

### Step 3 Commit and push the generated workflow file to your repository.


## Example of a pipeline.yaml configuration:

pipeline:
  build:
    - name: Install Dependencies
      run: npm install
  test:
    - name: Run Unit Tests
      run: npm test
  deploy:
    - name: Deploy to Production
      if: github.ref == 'refs/heads/main'
      run: ./deploy.sh production


### Project Directory Structure
```
cicd-pipeline-config-manager/
│
├── generate_workflow.py       # Main script to generate GitHub Actions workflow
├── pipeline.yaml             # Sample YAML configuration file
├── README.md                 # Project documentation
└── .github/
    └── workflows/            # Directory where the generated workflow will be saved
```


## License
This project is licensed under the MIT License - see the LICENSE file for details.




