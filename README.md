Ansible Role: Jenkins on OpenShift
=========

Ansible Role for deploying Jenkins CI engine on OpenShift


Role Variables
------------

|Variable                    | Default Value     | Description   |
|----------------------------|-------------------|---------------|
|`jenkins_max_mem`           | 2Gi               | Max memory allocated to Jenkins container |
|`jenkins_min_mem`           | 512Mi             | Min memory allocated to Jenkins container |
|`jenkins_max_cpu`           | 1                 | Max cpu allocated to Jenkins container |
|`jenkins_min_cpu`           | 200m              | Min cpu allocated to Jenkins container |
|`jenkins_image_tag`         | latest            | Jenkins image tag to deploy. Specify tag for either [OpenShift Container Platform](https://access.redhat.com/containers/?tab=tags#/registry.access.redhat.com/openshift3/jenkins-2-rhel7) or [OpenShift Origin](https://hub.docker.com/r/openshift/jenkins-2-centos7/tags/)|
|`jenkins_image_repository`  | registry.access.redhat.com/openshift3/jenkins-2-rhel7 | Jenkins image repository |
|`jenkins_image_force_import`| false             | Force re-import of the Jenkins image version `jenkins_image_tag` from `jenkins_image_repository` repo |
|`project_name`              | jenkins           | OpenShift project name for the Jenkins container  |
|`project_display_name`      | Jenkins           | OpenShift project display name for the Jenkins container  |
|`project_desc`              | Jenkins CI Engine | OpenShift project description for the Jenkins container |
|`project_annotations`       | -                 | OpenShift project annotations for the Jenkins container |
|`openshift_cli`             | oc                | OpenShift CLI command and arguments (e.g. auth)       | 


Example Playbook
------------

```
name: Example Playbook
hosts: localhost
tasks:
- import_role:
    name: siamaksade.openshift_jenkins
  vars:
    jenkins_image_tag: "v3.7"
    jenkins_image_force_import: true
    project_name: "cicd-project"
    openshift_cli: "oc --server http://master:8443"
```