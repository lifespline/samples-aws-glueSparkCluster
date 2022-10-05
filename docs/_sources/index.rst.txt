.. raw:: html

   <a href="https://github.com/lifespline/samples-aws-glueSparkCluster.git"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_darkblue_121621.png?resize=149%2C149" class="attachment-full size-full" alt="Fork Me On Github" data-recalc-dims="1"></a>

==========================================
Lifespline AWS Samples: Glue Spark Cluster
==========================================

The sample shows how to set up an AWS Glue Spark job, consuming data to and from AWS S3. The job runs first locally with a spark docker container. The container is published to the AWS Registry and consumed directly from the Glue Spark job.

Data
----

The data is specified in :download:`mock data <../../static/gen_mock_data.py>`.

.. automodule:: gen_mock_data
   :members:

.. toctree::
   :maxdepth: 1
   :caption: Contents:

   src/architecture
   src/contributing
   src/literature
