# CI-CD-Pipeline-Configuration-Manager-YAML

Simplify and automate the setup of CI/CD pipelines using GitHub Actions. 
This tool allows you to define build, test, and deploy stages using a single YAML configuration file, making it easy to replicate and manage pipelines across multiple projects.

## Features
✨ YAML-based Configuration: Define your CI/CD pipeline stages (build, test, deploy) in a simple YAML file. <br>
✨ Automated Workflow Generation: Automatically generates GitHub Actions workflow files based on your configuration. <br>
✨ Supports Multiple Environments: Easily configure pipelines for different environments (development, staging, production). <br>
✨ Flexible Customization: Customize build steps, testing commands, and deployment procedures. <br>



## How to Use

### Prerequisites
- Python 3.x
- Install PyYAML library: `pip install pyyaml`
- GitHub repository with GitHub Actions enabled

### Installation
1. Clone repository:  `git clone https://github.com/your-username/cicd-pipeline-config-manager.git`
2. Move to directory: `cd cicd-pipeline-config-manager`
3. Install required Python packages: `pip install -r requirements.txt`


### Step 1: Create a YAML configuration file named pipeline.yaml in the root of your project.
The YAML configuration file is organized under the pipeline key, which contains three main stages: build, test, and deploy, making it easy to manage and extend.

⚠️ _Customize it by adding additional commands or changing the paths, names and dependencies accordingly to your setup_ 

```
pipeline:
  build: # Prepare your application by installing necessary dependencies or tools.
    - name: Install Dependencies
      run: pip install flask

    - name: Set Up Python Virtual Environment
    - run: python3 -m venv venv1 # Creates a virtual environment named 'venv1'

    - name: Activate Virtual Environment
    - run: source venv1/bin/activate

  test: # Runs your unit tests to ensure code quality.
    - name: Run Unit Tests
      run: npm test # Example: Run unit tests; replace with your test command.

  deploy: # Handles deploying if conditions are met (e.g., upload files, restart services, trigger hooks).
    - name: Deploy to Production
      if: github.ref == 'refs/heads/main' # Only deploys when changes are pushed to the 'main' branch.
      run: ./deploy.sh production # Executes the 'deploy.sh' script with 'production' as an argument.
```

### Step 2: Run the script to generate the GitHub Actions workflow file.

```
python generate_workflow.py
```

### Step 3: Commit and push the generated workflow file to your repository.


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




