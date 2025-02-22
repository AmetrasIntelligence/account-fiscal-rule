=================================
Ecotax Management (with Odoo tax)
=================================

.. 
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! This file is generated by oca-gen-addon-readme !!
   !! changes will be overwritten.                   !!
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! source digest: sha256:bc334c7e37ef90dd515f13a029b06a4189614d22d962aa9f3837d3c9fd929dad
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

.. |badge1| image:: https://img.shields.io/badge/maturity-Beta-yellow.png
    :target: https://odoo-community.org/page/development-status
    :alt: Beta
.. |badge2| image:: https://img.shields.io/badge/licence-AGPL--3-blue.png
    :target: http://www.gnu.org/licenses/agpl-3.0-standalone.html
    :alt: License: AGPL-3
.. |badge3| image:: https://img.shields.io/badge/github-OCA%2Faccount--fiscal--rule-lightgray.png?logo=github
    :target: https://github.com/OCA/account-fiscal-rule/tree/16.0/account_ecotax_tax
    :alt: OCA/account-fiscal-rule
.. |badge4| image:: https://img.shields.io/badge/weblate-Translate%20me-F47D42.png
    :target: https://translation.odoo-community.org/projects/account-fiscal-rule-16-0/account-fiscal-rule-16-0-account_ecotax_tax
    :alt: Translate me on Weblate
.. |badge5| image:: https://img.shields.io/badge/runboat-Try%20me-875A7B.png
    :target: https://runboat.odoo-community.org/builds?repo=OCA/account-fiscal-rule&target_branch=16.0
    :alt: Try me on Runboat

|badge1| |badge2| |badge3| |badge4| |badge5|

This module allows to compute the ecotax amounts from Odoo tax mechanism.
The advantages compared to the base account_ecotax module is that it allows to : 
- Manage ecotax amount as included or excluded from the price of the product
- Isolate the amount of the ecotax in a specific accounting account (set on the  tax)

Then the ecotax amounts are not considered as turnover, which could be good or not depending on your country's legislation or accountant preferences.

**Table of contents**

.. contents::
   :local:

Usage
=====

1. Create a tax group named **"Ecotaxes"**. The sequence must be lower than other tax groups.
   - Set the **Preceding Subtotal** field to **"Without Ecotax"**.

2. Create two taxes named **"Fixed Ecotax"** and **"Weight-Based Ecotax"**.
   - Check the **Ecotax** checkbox.
   - Set the correct Python code:

     - For the fixed ecotax:

       .. code-block:: python

          result = quantity and product.fixed_ecotax * quantity or 0.0

     - For the weight-based ecotax:

       .. code-block:: python

          result = quantity and product.weight_based_ecotax * quantity or 0.0

   - Check the **Included in Base Amount** option.
   - The sequence for Ecotax must be lower than the VAT tax.

3. For VAT taxes, check the **Base Affected by Previous Taxes?** option.

4. Add an ecotax classification via the menu **Accounting > Configuration > Taxes > Ecotax Classification**.

   - The ecotax classification can be either a fixed ecotax or a weight-based ecotax.
   - Ecotax classification information can be used for legal declarations.
   - For the fixed ecotax, the ecotax amount is used as a default value, which can be overridden on the product.
   - For the weight-based ecotax, define one ecotax by a coefficient applied to the weight (depending on the product's materials).
   - Set the appropriate tax in the **Sale Ecotax** field.

5. Assign one or more ecotax classifications to a product.

   - The ecotax amount can also be manually overridden on the product.

Bug Tracker
===========

Bugs are tracked on `GitHub Issues <https://github.com/OCA/account-fiscal-rule/issues>`_.
In case of trouble, please check there if your issue has already been reported.
If you spotted it first, help us to smash it by providing a detailed and welcomed
`feedback <https://github.com/OCA/account-fiscal-rule/issues/new?body=module:%20account_ecotax_tax%0Aversion:%2016.0%0A%0A**Steps%20to%20reproduce**%0A-%20...%0A%0A**Current%20behavior**%0A%0A**Expected%20behavior**>`_.

Do not contact contributors directly about support or help with technical issues.

Credits
=======

Authors
~~~~~~~

* Akretion

Contributors
~~~~~~~~~~~~

* Mourad EL HADJ MIMOUNE <mourad.elhadj.mimoune@akretion.com>
* Florian da Costa <florian.dacosta@akretion.com>

Maintainers
~~~~~~~~~~~

This module is maintained by the OCA.

.. image:: https://odoo-community.org/logo.png
   :alt: Odoo Community Association
   :target: https://odoo-community.org

OCA, or the Odoo Community Association, is a nonprofit organization whose
mission is to support the collaborative development of Odoo features and
promote its widespread use.

.. |maintainer-mourad-ehm| image:: https://github.com/mourad-ehm.png?size=40px
    :target: https://github.com/mourad-ehm
    :alt: mourad-ehm
.. |maintainer-florian-dacosta| image:: https://github.com/florian-dacosta.png?size=40px
    :target: https://github.com/florian-dacosta
    :alt: florian-dacosta

Current `maintainers <https://odoo-community.org/page/maintainer-role>`__:

|maintainer-mourad-ehm| |maintainer-florian-dacosta| 

This module is part of the `OCA/account-fiscal-rule <https://github.com/OCA/account-fiscal-rule/tree/16.0/account_ecotax_tax>`_ project on GitHub.

You are welcome to contribute. To learn how please visit https://odoo-community.org/page/Contribute.
