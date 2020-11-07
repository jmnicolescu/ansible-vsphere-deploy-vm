# Deploy / Destroy /Tag VMware vSphere Virtual Machines using Ansible

### Configuration

├── deploy_vm.yml
├── destroy_vm.yml
├── helpers
│   ├── check_datastore_free_space.yml
│   ├── create_folders.yml
│   ├── create_tags.yml
│   ├── remove_folders.yml
│   └── remove_tags.yml
├── Readme_gpg.md
├── Readme.md
└── variables.yml


File Name: deploy_vm.yml - Deploy a new VM from a template.

File Name: destroy_vm.yml - Power OFF and Remove an existing VM.

File Name: helpers/create_tags.yml - Create a VMware category and VM tag. Assign the tag to a VM.

### Helpers

File Name: helpers/create_folders.yml - Create a VM folder and sub folder on given datacenter.

File Name: check_datastore_free_space.yml - Display datastore usage. Fails if datastore free space is less than datastore_freespace_limit

### Requirements

1. Variables vsphere_tag_category and vsphere_tag must exist
   To create the category and tag execute: cd helpers  &&  ansible-playbook create_tags.yml

2. Variables deploy_vsphere_folder and deploy_vsphere_sub_folder must exist
   To create vSphere folder and sub-folder execute: cd helpers && ansible-playbook create_folders.yml


### Execution

### Deploy a new VM from a template

    Check Mode (Dry Run)

    \> ansible-playbook -C deploy_vm.yml

    Execute

    \> ansible-playbook deploy_vm.yml 

### Power OFF and Remove an existing VM 

    Check Mode (Dry Run)

    \> ansible-playbook -C destroy_vm.yml

    Execute

    \> ansible-playbook remove_vm.yml


### Encrypting a string using GPG and Pass

If the vCenter credentials are managed via GPG and Pass, set the apropiate environment variables

export TF_VAR_provider_vsphere_host=$(pass provider_vsphere_host)

export TF_VAR_provider_vsphere_user=$(pass provider_vsphere_user)

export TF_VAR_provider_vsphere_password=$(pass provider_vsphere_password)
