.. _7-Configure-Office-365-with-SpamExperts:

Configure Office 365 with SpamExperts
=====================================

When using inbound filtering with an Office 365 account, you simply need
to make sure that the route you have set for your domain is the
Office365 mail- server hostname.

In your Office 365 Environment, we recommend to create a "**Transport
Rule**\ " for our delivery IP's. To do this you need to do the
following:

-  Click **Admin** and choose **Exchange** from the menu.
-  Select **Mail Flow**
-  Under Rules, click the **+button** and choose **Create New Rule**.
-  Add a Name for your Rule '*SpamExperts*\ '.
-  Click \ **More Options**
-  Create Rule "*If The sender* >>\_ IP address is in any of these
   ranges or exactly matches\_".
-  Add the SpamExperts IP's in the box provided\*.
-  Click **+.**
-  Click **OK.**
-  In the "*Do the following*\ " part, select "***Modify the message
   properties***\ " >> "*S\ **et the spam confidence level (SCL)***\ "
   >> "***Specify SCL***\ " >> "***Bypass spam filtering***\ "
-  Click **OK.**
-  Click **Save** to save the new transport rule.

\*For Hosted Cloud users, The IP's that you need to add can be found by
looking up our hostname "delivery.antispamcloud.com".
