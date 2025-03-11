# Implementing IaC with Ansible on Google Cloud Platform (GCP)

## **Introduction**
Ansible can automate the provisioning of infrastructure on GCP using the `gcp_compute` module. This guide walks through the steps to create a Google Compute Engine (GCE) instance using an Ansible playbook.

## **1. Prerequisites**
Before proceeding, ensure you have:
- **A Google Cloud Platform (GCP) account** with billing enabled.
- **Google Cloud SDK installed and configured** (`gcloud auth application-default login`).
- **Ansible installed** (`pip install ansible`).
- **Service account credentials (`gcp-service-account.json`)** for authentication.

## **2. Create an Ansible Playbook**
The playbook provisions a GCE instance with a specified machine type and image.

### **File: `gce-instance.yml`**
```yaml
- name: Create a GCE instance
  hosts: localhost
  connection: local
  gather_facts: no
  vars:
    gcp_project: "your-gcp-project-id"
    gcp_zone: "us-central1-a"
    machine_type: "n1-standard-1"
    image: "debian-11"
    instance_name: "ansible-gcp-instance"

  tasks:
    - name: Create an instance
      google.cloud.gcp_compute_instance:
        name: "{{ instance_name }}"
        machine_type: "{{ machine_type }}"
        zone: "{{ gcp_zone }}"
        project: "{{ gcp_project }}"
        auth_kind: "serviceaccount"
        service_account_file: "gcp-service-account.json"
        disks:
          - auto_delete: true
            boot: true
            initialize_params:
              source_image: "projects/debian-cloud/global/images/family/{{ image }}"
        network_interfaces:
          - network: "global/networks/default"
        state: present
      register: gce_instance

    - name: Display instance details
      debug:
        var: gce_instance


Run the Ansible Playbook
Execute the following command:

sh
ansible-playbook gce-instance.yml
4. Verify the Instance in GCP
Check the instance on Google Cloud Console or using:

sh
gcloud compute instances list
5. Delete the Instance (Optional)
To remove the instance:

sh
ansible-playbook gce-instance.yml -e "state=absent"
yaml

---

## **3. Create the Ansible Playbook (`gce-instance.yml`)**  

### **Create the File**  
```sh
touch gce-instance.yml
Open and Edit the File
sh
code gce-instance.yml
Paste the Ansible Playbook Code
Copy and paste the YAML playbook from step 2.

