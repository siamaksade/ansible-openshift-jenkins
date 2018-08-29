Ansible Role: Jenkins on OpenShift
[![Build Status](https://travis-ci.org/siamaksade/ansible-openshift-jenkins.svg?branch=master)](https://travis-ci.org/siamaksade/ansible-openshift-jenkins)
=========

Ansible Role for deploying Jenkins CI engine on OpenShift


Role Variables
------------

|Variable                    | Default Value     | Description   |
|----------------------------|-------------------|---------------|
|`update_jenkins_templates`  | false             | Update default Jenkins templates and adjust cpu and mem resources (requires cluster admin) |
|`jenkins_template_disable_admin_monitors` | false | Disable cpu-intensive update tasks on Jenkins bootstrap which pronolgs the start up time |
|`deploy_jenkins`            | true              | Deploy Jenkins |
|`jenkins_service_name`      | jenkins           | Jenkins service name on OpenShift  |
|`jenkins_max_mem`           | 2Gi               | Max memory allocated to Jenkins container |
|`jenkins_min_mem`           | 512Mi             | Min memory allocated to Jenkins container |
|`jenkins_max_cpu`           | 1                 | Max cpu allocated to Jenkins container |
|`jenkins_min_cpu`           | 200m              | Min cpu allocated to Jenkins container |
|`jenkins_image_tag`         | latest            | Jenkins image tag to deploy. Specify tag for either [OpenShift Container Platform](https://access.redhat.com/containers/?tab=tags#/registry.access.redhat.com/openshift3/jenkins-2-rhel7) or [OpenShift Origin](https://hub.docker.com/r/openshift/jenkins-2-centos7/tags/)|
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
    project_name: "cicd-project"
    openshift_cli: "oc --server http://master:8443"
```