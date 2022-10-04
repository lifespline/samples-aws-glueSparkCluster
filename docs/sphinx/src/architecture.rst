.. raw:: html

   <a href="https://github.com/lifespline/samples-aws-gluesparkcluster.git"><img loading="lazy" width="149" height="149" src="https://github.blog/wp-content/uploads/2008/12/forkme_left_darkblue_121621.png?resize=149%2C149" class="attachment-full size-full" alt="Fork me on GitHub" data-recalc-dims="1"></a>

============
Architecture
============

S3 Bucket
---------

* bucket name: ``samples-aws-gluesparkcluster-docs``
* region: ``<region>``
* policy: :ref:`policy <s3_policy>` CloudFront will provide you with the policy statement after creating the distribution (?)
* block public access: ``Block all public access``

.. _s3_policy:

.. code-block:: json

   {
       "Version": "2008-10-17",
       "Id": "PolicyForCloudFrontPrivateContent",
       "Statement": [
           {
               "Sid": "AllowCloudFrontServicePrincipal",
               "Effect": "Allow",
               "Principal": {
                   "Service": "cloudfront.amazonaws.com"
               },
               "Action": "s3:GetObject",
               "Resource": "arn:aws:s3:::samples-aws-gluesparkcluster-docs/*",
               "Condition": {
                   "StringEquals": {
                       "AWS:SourceArn":    "arn:aws:cloudfront::<account>:distribution/<hash>"
                   }
               }
           }
       ]
   }

CloudFront
----------

* distribution name: ``samples-aws-gluesparkcluster-dist``
* origin: ``sample-aws-cloudfrontdocs-docs.s3.<region>.amazonaws.com``
* origin access: ``Origin access control settings`` (restrict access to only CloudFront)
    * control setting:
        * name: ``sample-aws-cloudfrontdocs-docs.s3.<region>.amazonaws.com``
        * sign requests: ``Yes``
* enable origin shield: ``No`` (improve the cache hit ratio of your CloudFront distribution)

Docs
----

Get the cloudfront distribution domain name ``https://<hash>.cloudfront.net`` and access the static docs at ``https://<hash>.cloudfront.net/index.html``.