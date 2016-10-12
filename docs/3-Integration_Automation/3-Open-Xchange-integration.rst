.. _3-Open-Xchange-integration:

Open-Xchange integration
========================

Open-Xchange App Suite 7.6+
===========================

For details on how to integrate SpamExperts on your existing
Open-Xchange server, please
see \ `here <http://oxpedia.org/wiki/index.php?title=Spamexperts>`__

Transparent integration
=======================

The SpamExperts Local Cloud solution can be transparently integrated
with Open-Xchange. This allows you to use the professional antispam
filtering of SpamExperts, whilst benefiting from the powerful
Open-Xchange frontend. To achieve this, only a few steps are required:

1. A global Sieve filtering rule should be added to your Open-Xchange
   setup, which automatically classifies each email with a
   "**X-Recommended-Action: reject**\ " header as spam
2. A small workaround can optionally be installed which will report
   emails classified as spam/not spam in Open-Xchange back to the
   SpamExperts systems to automatically fine-tune the filtering further

External integration
====================

OpenXchange can provide you with a special SpamExperts 'AntiSpam'
function which allows one-click-login access to the SpamExperts control
panel directly from Open-Xchange.

.. figure:: /_static/images/oxiconSE.png
   :alt: 

Clicking this will bring you directly into your configured SpamExperts
Control Panel.

.. figure:: /_static/images/ox4.png
   :alt: 

For a description of the options available on the SpamExperts Control
Panel, please see our detailed knowledgebase articles
:ref:`here <8-Control_Panel_Documentation>`.

Setting up IMAP folders
-----------------------

To set up the your SpamExperts IMAP folders, simply follow these steps:

Create a new account by clicking on the **E-Mail side option**, then
click on **Accounts** & **New**;

.. figure:: /_static/images/addimapox.png
   :alt: 

Now add the details of you IMAP in the account settings page.
