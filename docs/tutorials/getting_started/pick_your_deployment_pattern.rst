.. _getting_started__customize_your_deployment:

Customize your deployment
=========================

At this point, you have your first, working deployment of Great Expectations. You've also been introduced to the foundational concepts in the library: :ref:`Data Contexts`, :ref:`Datasources`, :ref:`Expectations`, :ref:`Profilers`, :ref:`Data Docs`, :ref:`Validation`, and :ref:`Checkpoints`.

Congratulations! You're off to a very good start.

The next step is to customize your deployment by upgrading specific components of your deployment. :ref:`Data Contexts` make this modular, so that you can add or swap out one component at a time. Most of these changes are quick, incremental steps---so you can upgrade from a basic demo deployment to a full production deployment at your own pace and be confident that your Data Context will continue to work at every step along the way.

This last section of the :ref:`getting_started` tutorial is designed to present you with clear options for upgrading your deployment. For specific implementation steps, please check out the linked :ref:`how_to_guides`.

Components
--------------------------------------------------

Here's an overview of the components of a typical Great Expectations deployment:

* Great Expectations configs and metadata 

    * :ref:`Options for storing Great Expectations configuration`
    * :ref:`Options for storing Expectations`
    * :ref:`Options for storing Validation Results`

* Integrations to related systems

    * :ref:`Additional Datasources and Generators`
    * :ref:`Options for hosting Data Docs`
    * :ref:`Additional Validation Operators and Actions`
    * :ref:`Options for triggering Validation`

..    * Key workflows
..
..        * :ref:`Creating and editing Expectations`
..        * :ref:`Triggering validation`


Options for storing Great Expectations configuration
----------------------------------------------------

The simplest way to manage your Great Expectations configuration is usually by committing ``great_expectations/great_expectations.yml`` to git. However, it's not usually a good idea to commit credentials to source control. In some situations, you might need to deploy without access to source control (or maybe even a file system).

Here's how to handle each of those cases:

* :ref:`How to use environment variables to populate credentials`
* :ref:`How to populate credentials from a secrets store`
* :ref:`How to instantiate a Data Context without a yml file`


Options for storing Expectations
--------------------------------

Many teams find it convenient to store Expectations in git. Essentially, this approach treats Expectations like test fixtures: they live adjacent to code and are stored within version control. git acts as a collaboration tool and source of record.

Alternatively, you can treat Expectations like configs, and store them in a blob store. Finally, you can store them in a database.

* :ref:`How to configure an Expectation store in Amazon S3`
* :ref:`How to configure an Expectation store in GCS`
* :ref:`How to configure an Expectation store in Azure blob storage`
* :ref:`How to configure an Expectation store to postgresql`


Options for storing Validation Results
--------------------------------------
By default, Validation Results are stored locally, in an uncommitted directory. This is great for individual work, but not good for collaboration. The most common pattern is to use a cloud-based blob store such as S3, GCS, or Azure blob store. You can also store Validation Results in a database.

* :ref:`How to configure a Validation Result store on a filesystem`
* :ref:`How to configure a Validation Result store in S3`
* :ref:`How to configure a Validation Result store in GCS`
* :ref:`How to configure a Validation Result store in Azure blob storage`
* :ref:`How to configure a Validation Result store to postgresql`


Additional DataSources and Generators
-------------------------------------

Great Expectations plugs into a wide variety of Datasources, and the list is constantly getting longer. If you have an idea for a Datasource not listed here, please speak up in `the public discussion forum <discuss.greatexpectations.io>`__.

* :ref:`How to configure a Pandas/filesystem Datasource`
* :ref:`How to configure a Pandas/S3 Datasource`
* :ref:`How to configure a Redshift Datasource`
* :ref:`How to configure a Snowflake Datasource`
* :ref:`How to configure a BigQuery Datasource`
* :ref:`How to configure a Databricks Azure Datasource`
* :ref:`How to configure an EMR Spark Datasource`
* :ref:`How to configure a Databricks AWS Datasource`
* :ref:`How to configure a self managed Spark Datasource`


Options for hosting Data Docs
-----------------------------

By default, Data Docs are stored locally, in an uncommitted directory. This is great for individual work, but not good for collaboration. A better pattern is usually to deploy to a cloud-based blob store (S3, GCS, or Azure blob store), configured to share a static website.

* :ref:`How to host and share Data Docs on a filesystem`
* :ref:`How to host and share Data Docs on S3`
* :ref:`How to host and share Data Docs on Azure Blob Storage`
* :ref:`How to host and share Data Docs on GCS`


Additional Validation Operators and Actions
-------------------------------------------

Most teams will want to configure various :ref:`Validation Actions` as part of their deployment.

* :ref:`How to re-render Data Docs as a Validation Action`
* :ref:`How to store Validation Results as a Validation Action`
* :ref:`How to trigger slack notifications as a Validation Action`
* :ref:`How to implement a custom Validation Action`

Modifying :ref:`Validation Operators` themselves is more advanced work. You can learn how here.

* :ref:`How to configure a Validation Operator`
* :ref:`How to configure a WarningAndFailureExpectationSuitesValidationOperator`
* :ref:`How to configure an ActionListValidationOperator`
* :ref:`How to implement a custom Validation Operator`

.. Creating and editing Expectations
.. ---------------------------------
.. 
.. #FIXME: Need words here.
.. 
.. #FIXME: Need list here, after we wrangle the how-to guides for creating and editing Expectations.

Options for triggering Validation
---------------------------------

There are two primary patterns for deploying Checkpoints. Sometimes Checkpoints are executed during data processing (e.g. as a task within Airflow). From this vantage point, they can control program flow. Sometimes Checkpoints are executed against materialized data. Great Expectations supports both patterns. There are also some rare instances where you may want to validate data without using a Checkpoint.

* :ref:`How to run a Checkpoint in Airflow`
* :ref:`How to run a Checkpoint in python`
* :ref:`How to run a Checkpoint in terminal`
* :ref:`How to validate data without a Checkpoint`
