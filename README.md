<p align="center">
  <img alt="NSIDC logo" src="https://nsidc.org/themes/custom/nsidc/logo.svg" width="150" />
</p>


# Converting JIRA Tickets to GitHub Issues

This software will allow JIRA and Github user to convert JIRA tickets to Github issues while maintaing as many features as possible. Currently, the tool transfers the JIRA title, description, checklist, labels, and status.

## Level of Support

* This repository is fully supported by NSIDC. If you discover any problems or bugs,
  please submit an Issue. If you would like to contribute to this repository, you may fork
  the repository and submit a pull request. 
* This repository is not actively supported by NSIDC but we welcome issue submissions and
  pull requests in order to foster community contribution.

See the [LICENSE](LICENSE) for details on permissions and warranties. Please contact
nsidc@nsidc.org for more information.


## Requirements

* JIRA Ticket XML
* Access to GitHub repository
* Python installed locally
* Anaconda and Conda installed locally


## Conda Environment Setup

This section will serve as a guide to set up the proper conda environment with the required libraries.

1. Clone this repository into a directory of your choosing
2. Verify you have [conda installed](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html): open a terminal and run `conda --version`. If a version number is returned, you have conda or miniconda installed.
3. Path to where you cloned the repository in the terminal of your choosing
4. Run the command `conda env create -f environment.yml` to create a new environment with the necessary libraries
5. Accept the creation and allow the dependencies to be installed
6. Activate the new environment with `conda activate JG-ETL` and have fun! 

**Other Conda Notes:**
- Use `conda --version` to check the version of conda
- Use `conda env list` to see your current conda environments
- Use `conda remove -n JG-ETL --all` to remove the environment
- Use `conda env update -f environment.yml` to update the environment after any changes to the environment.yml file


## Usage

This tool is made to run on the command line. The user needs to input four variables to get started: a path to a JIRA issues .xml file, the organization or repository owner username, the name of the repository, and a Personal Access Token (PAT).

### [Personal Access Tokens (PATs)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens): 

GitHub PATs are a method for authenticating with the GitHub REST API. They are  strings of random letters and numbers generated by a GitHub user that allow that user to perform actions with GitHub, without the need for a website (in our case GitHub issues). The user decides the permissions of a PAT before creation and once a token is created, it will have those permissions until it expires (or is deleted).
There are two different types of GitHub PAT tokens: classic and fine grain. Fine grain tokens only allow access to repositories owned by the creator of the token and allow for more specific permissions for those repositories. Classic PATs, on the other hand, allow access to all repositories within the organizations that you have access to, as well as all personal repositories in your personal account. This makes them less secure, but for our purposes, it allows a user to upload issues to a repository where they are not the owner or in the organization.

Depending on the use case of the tool, these are the permissions needed for the PAT:
* If you own the repository:
    * Use a fine-grain PAT
    * Under Repository Access, select "Only Select Repositories" and the specific repositories you are uploading issues to
    * In the "Repository Permissions" drop-down, set "Issues" access to read and write (Note: this will automatically set "Metadata" to read-only)
    * Be sure to copy the PAT after creation

* If you do not own the repository or are not in the organization (you still need to be a collaborator on the repository):
    * Use a classic PAT
    * Under "Select Scopes", check "repo", to grant full access to all repositories you are a collaborator on
    * Be sure to copy the PAT after creation


### Using the Tool:

1. Open a terminal
2. Verify you have [python installed](https://www.python.org/downloads/): run `python --version`. If a version number is returned, you have python installed.
3. Path to where this repository is cloned
4. Run `python GitHubAPI.py`
5. Follow the prompts


## Credit

This content was developed by the National Snow and Ice Data Center with funding from
multiple sources.
