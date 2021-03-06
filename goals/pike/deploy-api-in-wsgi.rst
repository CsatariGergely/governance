.. -*- mode: rst -*-

================================================
 Control Plane API endpoints deployment via WSGI
================================================

In some projects, API services can be run:

#. As a Python command that runs a web server (e.g. wsgiref or werkzeug).
#. As a WSGI application hosted by performant web servers (e.g. Apache with
   mod_wsgi or Nginx with uWSGI).

When a project provides a WSGI application the API service gains flexibility
in terms of deployment, performance, configuration and scaling.

Gerrit Topic
============

To facilitate tracking, commits related to this goal should use the
gerrit topic::

  goal-deploy-api-in-wsgi

Completion Criteria
===================

For all projects:

#. Provide WSGI application script file(s) (e.g. to be used by web server).
   There shouldn't be any web server restriction and the application could be
   deploying to any web server that support WSGI applications.
#. Switch devstack jobs to deploy control-plane API services in WSGI with Apache.
   Usage of Apache is already the default in Devstack, let's keep using it
   for consistency unless there is some efforts to support another web server but
   this is not the case at this time.

References
==========

Reference documentation for the existing WSGI deployments:
* http://docs.openstack.org/developer/keystone/apache-httpd.html
* http://docs.openstack.org/developer/ceilometer/install/mod_wsgi.html

Current State / Anticipated Impact
==================================

On 12 Jan 2017 a review of git repositories owned by big tent project
showed the projects that don't support their control-plane API services deployed
via WSGI:

.. (emilien) I built this list based on my research. Please comment if
   something is wrong or missing.
   This list reflects the projects where API can't be deployed via WSGI.

* cloudkitty
* congress
* designate
* freezer
* glance
* kuryr
* magnum
* murano
* neutron
* octavia
* searchlight
* solum
* tacker
* trove
* vitrage
* watcher
* zun

.. (emilien) TODO

These projects already deploy devstack with API service via WSGI:

* aodh
* ceilometer
* cinder
* gnocchi
* ironic
* keystone
* mistral
* nova
* panko
* swift
* zaqar
* (...)

Project Teams
=============

barbican
--------

Planning Artifacts:

* https://blueprints.launchpad.net/barbican/+spec/goal-deploy-api-in-wsgi

Completion Artifacts:

Chef OpenStack
--------------

The Chef cookbooks do not provide any API directly, they consume
downstream packages, and thus are not directly affected by this goal.
When packages support deploying API services via WSGI, the
corresponding cookbooks use it.

Planning Artifacts: None

Completion Artifacts: None

cinder
------

Planning Artifacts:

Completion Artifacts:

cloudkitty
----------

Planning Artifacts:

Completion Artifacts:

Community App Catalog
---------------------

Planning Artifacts:

Completion Artifacts:

congress
--------

Planning Artifacts:

* https://bugs.launchpad.net/congress/+bug/1670517

Completion Artifacts:

designate
---------

Planning Artifacts:

Completion Artifacts:

Documentation
-------------

Planning Artifacts:

* https://blueprints.launchpad.net/openstack-manuals/+spec/document-api-endpoints-wsgi

Note: Dependent on upstream projects achieving deploy-api-in-wsgi goal.

Completion Artifacts:

dragonflow
----------

Planning Artifacts:

Completion Artifacts:

ec2-api
-------

Planning Artifacts:

Completion Artifacts:

freezer
-------

Planning Artifacts:

Completion Artifacts:

fuel
----

Planning Artifacts:

Completion Artifacts:

glance
------

Planning Artifacts:

* `Glance Spec Lite
  <http://specs.openstack.org/openstack/glance-specs/specs/pike/approved/glance/lite-specs.html>`_

Completion Artifacts:

heat
----

Planning Artifacts:

* Heat has no planning documents at this time since the support was
  introduced and enabled by default at Ocata.

Completion Artifacts:

* `heat <http://git.openstack.org/cgit/openstack/heat/commit/?id=6ef5fa9adc8886ed339132b5e5e27cee4000f762>`_

horizon
-------

Planning Artifacts:

Completion Artifacts:

I18n
----

Planning Artifacts:

* The I18n team does not have any API services and therefore has
  nothing to do

Completion Artifacts:

* None

Infrastructure
--------------

Planning Artifacts:

Completion Artifacts:

ironic
------

Planning Artifacts:

  RFE: https://bugs.launchpad.net/ironic/+bug/1513005

Completion Artifacts:

karbor
------

Planning Artifacts:

* https://bugs.launchpad.net/karbor/+bug/1681500

Completion Artifacts:

keystone
--------

Planning Artifacts:

* Keystone has no planning documents at this time since support was
  introduced prior to Kilo.

Completion Artifacts:

* http://git.openstack.org/cgit/openstack-dev/devstack/commit/?id=a00e5f8810b6ca3b0b5d63cc228125e19bc91955

kolla
-----

Planning Artifacts:

Completion Artifacts:

kuryr
-----

Planning Artifacts:

Completion Artifacts:

magnum
------

Planning Artifacts:

Completion Artifacts:

manila
------

Planning Artifacts:

Completion Artifacts:

mistral
-------

Planning Artifacts:

Completion Artifacts:

monasca
-------

Planning Artifacts:

* https://review.openstack.org/442365

Completion Artifacts:

* https://review.openstack.org/439577
* https://review.openstack.org/436890

murano
------

Planning Artifacts:

* `murano-api-bp <https://blueprints.launchpad.net/murano/+spec/murano-api-wsgi>`_

Completion Artifacts:

* https://review.openstack.org/#/c/442327/
* https://review.openstack.org/#/c/442936/

neutron
-------

Planning Artifacts:

* https://bugs.launchpad.net/neutron/+bug/1666779

Completion Artifacts:

* Expose neutron app as a wsgi script: https://review.openstack.org/#/c/409351/
* Enable neutron wsgi in devstack: https://review.openstack.org/#/c/439191/

nova
----

Planning Artifacts:

Nova is tracking the work in the `devstack-uwsgi etherpad`_. The placement
service already runs under mod_wsgi in devstack but that will be changed to
uwsgi. There is also a bug in nova-api that needs to be fixed before we can
deploy it under uswgi in devstack for testing.

.. _devstack-uwsgi etherpad: https://etherpad.openstack.org/p/devstack-uwsgi

Completion Artifacts:

octavia
-------

Planning Artifacts:

The octavia API is already implemented as a wsgi application, we just need to
setup the web server integration.  This is work in progress here:
https://review.openstack.org/440934

Completion Artifacts:

OpenStack Charms
----------------

Planning Artifacts:

Completion Artifacts:

OpenStack UX
------------

Planning Artifacts:

Completion Artifacts:

OpenStackAnsible
----------------

Planning Artifacts:

* https://blueprints.launchpad.net/openstack-ansible/+spec/goal-deploy-api-in-wsgi

NB Individual roles are dependent on the upstream project achieving the deploy-api-in-wsgi goal.

Completion Artifacts:

OpenStackClient
---------------

Planning Artifacts:

Completion Artifacts:

oslo
----

Planning Artifacts:

Completion Artifacts:

Packaging-deb
-------------

Planning Artifacts:

Completion Artifacts:

Packaging-rpm
-------------

Planning Artifacts:

Completion Artifacts:

Puppet OpenStack
----------------

Planning Artifacts:

Projects where we plan to add support:

* puppet-zaqar

Completion Artifacts:

Projects that already support WSGI deployments for API:

* puppet-aodh
* puppet-barbican
* puppet-ceilometer
* puppet-cinder
* puppet-gnocchi
* puppet-heat
* puppet-ironic
* puppet-keystone
* puppet-mistral
* puppet-nova
* puppet-panko
* puppet-vitrage

Quality Assurance
-----------------

Planning Artifacts:

* The only project that includes a python web application is the API part
  of OpenStack Health, which is not an OpenStack control plane service.
  OpenStack Health API is deployed as a WSGI application as part of OpenStack
  infra. Further details in https://etherpad.openstack.org/p/pike-qa-goals-wsgi.

Completion Artifacts:

* None

rally
-----

Planning Artifacts:

Completion Artifacts:

RefStack
--------

Planning Artifacts:

Completion Artifacts:

Release Management
------------------

Planning Artifacts:

* The Release management team doesn't have any API services and therefore
  has nothing to do

Completion Artifacts:

* None

requirements
------------

Planning Artifacts:

* The requirements team do not have any API services and therefore has
  nothing to do.

Completion Artifacts:

* None

sahara
------

Planning Artifacts:

* Update devstack plugin to deploy in WSGI with Apache
* Launchpad bug: https://bugs.launchpad.net/sahara/+bug/1673198

Completion Artifacts:
 * Enable wsgi jobs: https://review.openstack.org/#/c/454083/

searchlight
-----------

Planning Artifacts:

Completion Artifacts:

Security
--------

Planning Artifacts:

Completion Artifacts:

senlin
------

Planning Artifacts:

Completion Artifacts:

shade
-----

Planning Artifacts:

* The shade team does not have any API services and therefore has
  nothing to do.

Completion Artifacts:

* None

solum
-----

Planning Artifacts:

* https://blueprints.launchpad.net/solum/+spec/solum-api-under-wsgi

Completion Artifacts:

* Add wsgi script file: https://review.openstack.org/#/c/448400/
* Enable wsgi on devstack jobs: https://review.openstack.org/#/c/448410/

Stable branch maintenance
-------------------------

Planning Artifacts:

* The stable team doesn't have any code repositories and therefore has
  nothing to do.

Completion Artifacts:

* None

swift
-----

Planning Artifacts:

Completion Artifacts:

tacker
------

Planning Artifacts:

Completion Artifacts:

Telemetry
---------

Planning Artifacts:

Completion Artifacts:

tricircle
---------

Planning Artifacts:

Completion Artifacts:

tripleo
-------

Planning Artifacts:

During Pike, we plan to migrate some services under WSGI with Apache:

* Heat APIs
* Ironic API when https://bugs.launchpad.net/ironic/+bug/1608252 will
  be fixed.
* Mistral API when https://bugs.launchpad.net/mistral/+bug/1663368 will
  be fixed.
* Nova API when it will be officially supported by Nova team.

Completion Artifacts:

TripleO already deploy some services under WSGI with Apache:

* Aodh API
* Barbican
* Ceilometer API
* Cinder API
* Gnocchi API
* Keystone
* Nova Placement
* Panko API

trove
-----

Planning Artifacts:

* https://bugs.launchpad.net/trove/+bug/1681478

Completion Artifacts:

* https://review.openstack.org/455477

vitrage
-------

Planning Artifacts:

* None. The Vitrage devstack jobs already deploy the Vitrage API in WSGI
  with Apache

Completion Artifacts:

* None

watcher
-------

Planning Artifacts:

Completion Artifacts:

Watcher API may now works with mod-wsgi.
Patchset https://review.openstack.org/#/c/450740/ provided the following
changes:

* wsgi app script files, to run watcher-api under Apache HTTPd.
* updated devstack plugin to run watcher-api default with mod-wsgi.
* document to deploy watcher-api behind wsgi.

winstackers
-----------

Planning Artifacts:

Completion Artifacts:

zaqar
-----

Planning Artifacts:

Completion Artifacts:

zun
---

Planning Artifacts:

* https://blueprints.launchpad.net/zun/+spec/deploy-zun-api-in-wsgi

Completion Artifacts:

* Add wsgi script file: https://review.openstack.org/#/c/437190/
* Enable wsgi on devstack jobs: https://review.openstack.org/#/c/438774/
