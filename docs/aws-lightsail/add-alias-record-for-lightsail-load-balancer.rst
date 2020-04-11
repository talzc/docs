Point your domain to your Lightsail load balancer
=================================================

*Last updated: June 12, 2019*

After you `verify that you control the domain where you want to have
encrypted (HTTPS)
traffic <verify-tls-ssl-certificate-using-dns-cname-https.md>`__, you
need to add an address (A) record to your domain's DNS hosting provider
that points your domain to your Lightsail load balancer. In this guide,
we show you how to add the A record to a Lightsail DNS zone, and a
Amazon Route 53 hosted zone.

Add an A record in Lightsail
----------------------------

1. On the Lightsail home page, choose **Networking**.

2. Choose the DNS zone you want to manage.

3. If you haven't created any records yet, choose **Add record**.

If you already have CNAME or other DNS records, choose **Add another**.

1. For **Type**, choose the default record type (**A**).

2. For **Sub-domain**, type ``www`` in front of ``example.com`` or don't
   use a prefix if using an apex domain.

3. | For destination IP, choose your load balancer from the list of available load balancers.
   | |[Choose your load balancer and create an alias (A) record]|

4. Choose **Save**.

Add an A record in Route 53
---------------------------

1.  Open the `Amazon Route 53
    console <https://console.aws.amazon.com/route53/>`__.

2.  In the navigation pane, choose **Hosted Zones**.

3.  Choose the name of the hosted zone that has the domain name that you
    want to use to route traffic to your load balancer.

4.  Choose **Create Record Set**.

5.  For **Name**, type ``www`` in front of ``example.com`` or don't use
    a prefix if using an apex domain.

6.  Accept the default record (**A - IPv4 address**).

7.  For **Alias**, choose **Yes**.

8.  | Go to the Lightsail console and copy the **DNS name** from your load balancer management page.
    | |[DNS name on the load balancer management page]|

9.  Go back to the Amazon Route 53 console and paste the DNS name into
    the **Alias Target** field.

10. Accept the default value of **Simple** for **Routing Policy**, and
    leave **No** selected for **Evaluate Target Health**.

Lightsail already performs health checks on your load balancer. `Learn
more about health
checking <enable-set-up-health-checking-for-lightsail-load-balancer-metrics.md>`__

| Your record set should look something like this.
| |[Create a record set in Route 53 to point an alias to your Lightsail
load balancer]|

1. Choose **Create**.

.. |[Choose your load balancer and create an alias (A) record]| image:: https://s3-us-west-2.amazonaws.com/parkside-localized-docs-devo/v1/en_us/b3f6d19f6c5a2810c4336f10d978ee98/images/create-alias-a-record-for-lightsail-load-balancer.png
.. |[DNS name on the load balancer management page]| image:: https://s3-us-west-2.amazonaws.com/parkside-localized-docs-devo/v1/en_us/b3f6d19f6c5a2810c4336f10d978ee98/images/dns-name-on-load-balancer-management-page.png
.. |[Create a record set in Route 53 to point an alias to your Lightsail load balancer]| image:: https://s3-us-west-2.amazonaws.com/parkside-localized-docs-devo/v1/en_us/b3f6d19f6c5a2810c4336f10d978ee98/images/create-record-set-alias-record-route-53.png
