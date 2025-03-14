Checkov is a static code analysis tool for scanning infrastructure as code (IaC) files for misconfigurations that may lead to security or compliance problems. 

Checkov includes more than 750 predefined policies to check for common misconfiguration issues.
Link to pre-defined polcies- https://www.checkov.io/5.Policy%20Index/terraform.html

 Checkov also supports the creation and contribution of custom policies.

To create a GitHub Actions workflow stage specifically for running Checkov on infrastructure as code (IAC) files, the following example YAML configuration is to be followed. 

In this YAML configuration:

1.We defined a GitHub Actions workflow named "Checkov Workflow" that triggers on pushes to the main branch.

2.The checkov job runs on an ubuntu-latest runner.

3.Within the steps section:
    a. First, python packages is being installed to install checkov.
    b. Once Python package is being installed, then Checkov is being installed.
    c. Finally, Checkov is run on IAC code, specifying the path to het code using the -d flag. Make sure to replace /path/to/your/iac/code with the actual path to 
    infrastructure as code files.

4.This yaml can be added to an existing GitHub Actions workflow, or to a newly created workflow by placing this YAML configuration in a .github/workflows/checkov.yml file within the repository. Adjust the triggers and paths as needed for specific use case.

Note:
-d = IaC root directory (can not be used together with --file).

-s = Runs checks but always returns a 0 exit code.

--quiet = For the CLI output, display only failed checks. Also disables progress bars.

--framework = Filter scan to run only on specific infrastructure code frameworks [env var: CKV_FRAMEWORK]

-o = Report output format. Add multiple outputs by using the flag multiple times (-o result.xml -o cli)

--output-file-path = Name of the output folder to save the chosen output formats. Advanced usage: By using -o cli -o junitxml --output-file-path console,results.xml

retention-days: The lifecycle of the logs.

path: The path where artifacts of the pipeline are stored

