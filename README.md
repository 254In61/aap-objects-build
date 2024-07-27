## overview

REF : https://console.redhat.com/ansible/automation-hub/repo/published/ansible/controller/

Repository contains IAC(Infrastructure as code) that outomates the creation of aap resources :
- organization
- credentials
- project
- job templates
- notifications
- workflows 

## Design considerations
- Resource objects creation separated into unique roles.
- Ensures re-usability of the code and also makes it easy to unit-test each part of the code.

## How to use

The playbook is run from ansible-enabled node that that has access to the AAP environment.It is NOT run from the machine on which AAP is installed.

Step 1: Set env hosts for Automation Controller.

    export CONTROLLER_HOST=https://******

    export CONTROLLER_USERNAME=***

    export CONTROLLER_PASSWORD=***

    export CONTROLLER_VERIFY_SSL=true/false ** If SSL certs are to be validated or not.

    export ANSIBLE_GALAXY_SERVER_AUTOMATION_HUB_TOKEN='eyJhb......w2Q" 

   - To get the urls and token:
     log into Automation Hub > Ansible Automation Platform  > Automation Hub > Connect to Hub .. Load token to generate one if missing.

Step 2 : Git clone down this repository into an environment that has access to your AAP set-up.

Step 3 : Ensure your ansible.cfg has the galaxy configs setup as in the file.

Step 4 : Install the needed collections : $ ansible-galaxy collection install -r collections/requirements.yml

Step 5 : Confirm group_vars/*object-vars*.yml have all your values reflected correctly.

Step 6 : Run the playbook :$ ansible-playbook site.yml


## Important notes

- This code is fixed to building of 3 job templates mentioned. If you want more, consider editing the modules/job_templates.yml file.

- The playbooks/modules are all found in the modules/ directory.

- After playbook completes running, go to the created docker credential and edit the "Authentication URL" section to docker.io & de-select Verify SSL.

  ** If you don't do this right, no image will be pulled down from the registry , hence no execute enviroment for your templates to run.

## Author
Name: 254in61


