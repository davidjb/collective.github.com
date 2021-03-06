Introduction
============

`github/collective`_ started as an experiment in October 2010. Many
`Plone <http://plone.org>`_ developers have joined since then, which 
definitely shows that development using git is gaining popularity amongst Plonistas.

"Rules" on github/collective
============================

- Every member gets Github's ``Pull and Push`` permission to all repositories.

- Each repository has owners (team of repository owners) which have
  Administrative rights to it.

- Abuse should be reported by opening a ticket in the `collective.github.com`_ repository.

How to get access
=================

- Fork `collective.github.com`_ repository, edit ``permissions.cfg`` file, 
  commit and push it and send us a Pull Request (see section below for details).

- File a ticket that you want permission here:
  https://github.com/collective/collective.github.com/issues
  (may take longer to process than forking, because a human needs to work more here)

How to manage permissions and repositories
==========================================

Process Overview
----------------

Permissions are stored in `permissions.cfg`_ file in `collective.github.com`_
repository.

1. **Fork** the `collective.github.com <https://github.com/collective/collective.github.com>`_
   repository to your account and then 

2. **edit** the `permissions.cfg`_. If you're done 

3. **commit, push** and create a **pull request**. 

We scheduled a script that runs every 10min and checks for differences and
updates them. 

Inside `permissions.cfg`_ file you have a list of teams and repositories.
Team are sections starting with ``team:`` and repository is a section
starting with ``repo:``.

Instructions on editing permissions.cfg
---------------------------------------

Push access
  Add yourself to the ``contributors`` (or any other team)
  Find the section ``[team:contributors]`` and insert your github username in 
  alphabetical order.

  **Please not use the button on github website to create new repositories, 
  otherwise the admin team has to edit the permissions.cfg file manually because 
  of your laziness**

Create a new repository
  Add a new section in alphabetical order::

        [repo:NEW_REPOSITORY_NAME]
        teams = contributors
        owners = MY_USERNAME

Fork an existing repository
  In order to fork from another github user or organization add a new section::

        [repo:REPOSITORYNAME]
        fork = FROM_USERNAME_OR_ORGANISATIONNAME/REPOSITORYNAME
        teams = contributors
        owners = MY_USERNAME

Not owner anymore?
  You created a repository in past and now you are not owner anymore? Add 
  yourself to the ``owners =`` of the existing repository section.


**TODO:** script does not set owner the person who forked project or first
committer

How to migrate a repository from svn.plone.org
==============================================

Code in the `Plone Collective Subversion <http://svn.plone.org/svn/collective>`_
or in the `Plone Archetypes Subversion <http://svn.plone.org/svn/archetypes>`_
should be migrated to the Github collective if it is still used and development
happens.

If youre not the maintainer of the repository contact the current maintainer before.
If unsure ask at the plone-product-developers mailing-list.

Follow the steps below for migration.

1. Add the project as a new repository to github collective `as you would do for a
   new one <#instructions-on-editing-permissions-cfg>`_. Once the pull-request was
   accepted and the repository created go on with step two.

2. On your machine use `svn2git to migrate on your local machine
   <https://help.github.com/articles/importing-from-subversion>`_
   (follow also the links in there). Unfortunately Plone Administrators can not provide
   an authors file (mapping from user-names to e-mail addresses) for privacy reasons.

3. rename the trunk of the existing repository to OLD-trunk and place a
   MOVED-TO-GITHUB.txt at top level of the project in svn. Add a line with the url
   to the repository to the file.

4. Some housekeeping

   - Rename ``README.txt`` to ``README.rst``, update ``setup.py`` to reflect this change,

   - Update links in ``README.rst`` to point to Github project

   - Update links on `plone.org product page <http://plone.org/products>`_ to point to Github repository

   - optional: send a mail to the plone-product-developers mailing-list and
     additional/optional tweet about it, write a line at IRC, if worth write a
     blog post, ... to notify the community about it.



More information
================

.. toctree::
    :maxdepth: 2
    
    how_to_followcommits
    how_to_update_this_documentation
    new_to_git
    how_to_merge

.. _`collective.github.com`: https://github.com/collective/collective.github.com
.. _`permissions.cfg`: https://github.com/collective/collective.github.com/blob/master/permissions.cfg
.. _`github/collective`: http://github.com/collective

