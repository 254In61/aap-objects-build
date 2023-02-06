overview
========

Repository contains IAC(Infrastructure as code) that outomates the creation of organization, project, job templates,notifications and workflows in that order.

The idea is to make create idempotency in the building of the above mentioned.


How to use
==========

NB : The playbook is run from your dev environment or any server that has access to the AAP environment. It is NOT
     run from the AAP.

Step 1: Have the following variables configured as env variables or saved in your AAP.

    export TOWER_HOST=https://******

    export TOWER_USERNAME=***
    
    export TOWER_PASSWORD=***
    
    export TOWER_VERIFY_SSL=0

Step 2 : Git clone down this repository into an environment that has access to your AAP set-up.

Step 3 : Confirm group_vars/aap_vars.yml have all your values reflected correctly.

Step 4 : Run the playbook :$ ansible-playbook aap-build.yml


Important notes
===============
- This code is fixed to building of 5 job templates mentioned. If you want more, consider editing the modules/job_templates.yml file.

- The playbooks/modules are all found in the modules/ directory.

- After playbook completes running, go to the created docker credential and edit the "Authentication URL" section to docker.io & de-select Verify SSL.
  ** If you don't do this right, no image will be pulled down from the registry , hence no execute enviroment for your templates to run.



Author
======
Name: 254in61


