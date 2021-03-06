This conformance report is generated by the OpenShift CI infrastructure. The canonical source location for this test script is located at https://github.com/openshift/origin/blob/master/test/extended/conformance-k8s.sh

This file was generated by:

  Commit 40f2586508872b9d4e3d198839a2cd3df45faedf
  Tag    v4.1.0-2045-g40f2586

To recreate these results:

## Install an OpenShift cluster

The [try.openshift.com](https://try.openshift.com) service will walk you through deploying your first OpenShift cluster. For instructions on installing on bare metal, virtualization, and in public clouds [please visit the official documentation](https://docs.openshift.com/container-platform/4.3/welcome/index.html#cluster-installer-activities).

The directions below will get you started on AWS:

1. Ensure you have AWS credentials configured on your machine that allow you to provision EC2 instances, set up service accounts, and configure networking
2. Configure a DNS hosted zone via the Route53 interface
3. [Download a pull secret](https://cloud.redhat.com/openshift/install/aws/installer-provisioned) for the free OpenShift evaluation
3. [Download the OpenShift install binary](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/), unzip it, and run 

        openshift-install create cluster

    to start the installation wizard

After you have installed a cluster, you'll need to relax the default security rules so that the conformance tests can run as an administrative user. This has the side effect of allowing unprivileged users to run root level containers, which may not be appropriate in a production environment. The official conformance script performs these actions below:

1. Retrieve the `kubeconfig` file with administrator credentials from the cluster and set the environment variable KUBECONFIG

        export KUBECONFIG=PATH_TO_KUBECONFIG

2. Clone the OpenShift source repository and change to that directory:

        git clone https://github.com/openshift/origin.git
        cd origin

3. Place the `oc` binary for that cluster in your PATH
4. Run the conformance test:

        test/extended/conformance-k8s.sh

Nightly conformance tests are run against release branches and reported at https://openshift-gce-devel.appspot.com/builds/origin-ci-test/logs/periodic-ci-origin-conformance-k8s/
