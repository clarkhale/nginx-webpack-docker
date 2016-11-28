AngularJS static application served up with Nginx 1.8 server 
============================================================

This S2I image builds an AngularJS static application and serves it up
with nginx, providing several points to customize the nginx
configuration.

This image is a combination of the rh-nginx-18 image and the
rh-nodejs4 Dockerfiles from the Red Hat Software Collections Library
(RHSCL).

Configuration
-------------

The application can use three directories to directly influence the
nginx configuration:

| Path | Description |
| ---- | ----------- | 
| nginx-cfg/nginx.global.d/ | Configuration included at the global scope | 
| nginx-cfg/nginx.httpglobal.d/ | Configuration included at http block scope | 
| nginx-cfg/nginx.defaultserver.d/ | Configuration included in the default server running on port 8080 |

Any file ending in .conf will be included.  

Any file ending in .conf.erb will be treated as an Embedded Ruby
template, and will be processed at run time (NOT at build time).  If
needed, OpenShift environment variables can be pulled into the nginx
configuration using these erb templates.

