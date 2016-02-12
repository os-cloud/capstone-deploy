Deploying Capstone
==================

Deployment tooling for `Capstone <https://github.com/rackerlabs/capstone>`_.


Prior to deploying capstone, specific upstream dependencies need to be
resolved. To resolve these using ``ansible-galaxy`` run the following::

    ansible-galaxy install --role-file=ansible-role-requirements.yaml \
                           --ignore-errors --force

The ``deploy.yaml`` playbook will expect an inventory file which will look
like::

    [keystone_all]
    <keystone_endpoint_ip_address>

The playbook will also expect us to provide a ``capstone.conf``::

    [service_admin]
    username = <username>
    password = <password>
    project_id = <project_id>

This account is provided by Rackspace. Once the ``capstone.conf`` and
``inventory`` files are in place we're ready to deploy::

    ansible-playbook -i inventory deploy.yaml
