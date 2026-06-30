---
layout:     post
title:      "JBossWS 7.4.0.Final is released!"
subtitle:   ""
date:       May 28, 2026
author:     Fabio Burzigotti
---

In this release we upgraded Apache CXF to 4.1.6, aligned Jakarta and JBoss dependencies to WildFly, and moved 
to jboss-jakarta-xml-ws-api 4.0 spec.

Please try out this release, and let us know if you have any issues or questions.

### Release notes - JBoss Web Services - jbossws-cxf-7.4.0.Final

#### Bug

- [JBWS-4488](https://redhat.atlassian.net/browse/JBWS-4488) - jbossws-cxf - "JBWS024029: Cannot obtain destination 
 for ..." is thrown when trying to consume a web service having NLS characters in URL path
  
  - JBossWS-CXF can automatically handle URL-encoded paths containing National Language Symbols \(NLS\) or other non-ASCII characters.   
    The stack can automatically try to decode incoming request paths to match the registered endpoints.
    
    This behavior is disabled by default and can be controlled globally via the following system properties:
    
    - `org.jboss.ws.cxf.decodeUrlPath` - controls the default behavior across all deployments. The default value is `false`.
    - `org.jboss.ws.cxf.urlCharset` - controls the charset that will be used to decode the URL path. The default value is `UTF-8`.
    
    Such properties can be overridden per-deployment, that is, via the `jboss-webservices.xml`  
    descriptor, which take precedence over the system properties.  
    
    The `org.jboss.ws.cxf.urlCharset` system property should be aligned with Undertow's `URL\_CHARSET` configuration option.

#### Component Upgrade

- [JBWS-4493](https://redhat.atlassian.net/browse/JBWS-4493) - Move to jboss-jakarta-xml-ws-api_4.0_spec from jboss-jakarta-xml-ws-api_3.0_spec

- [JBWS-4503](https://redhat.atlassian.net/browse/JBWS-4503) - Align jakarta.* and jboss.* dependencies version to WildFly

- [JBWS-4512](https://redhat.atlassian.net/browse/JBWS-4512) - (jbossws-cxf) - Align wildfly* dependencies version to WildFly for jbossws-cxf-7.4.0 consolidation

- [JBWS-4515](https://redhat.atlassian.net/browse/JBWS-4515) - (jbossws-cxf) - Update JBossWS components to the latest released version for jbossws-cxf-7.4.0.Final consolidation

- [JBWS-4518](https://redhat.atlassian.net/browse/JBWS-4518) - (jbossws-cxf) - Upgrade Apache CXF version from 4.1.5 to 4.1.6

#### Task

- [JBWS-4487](https://redhat.atlassian.net/browse/JBWS-4487) - Upgrade Apache CXF dependencies to 4.1.5

  - Apache CXF was upgraded to 4.1.5, as the 4.0.x stream is no longer maintained, and the 4.2.0 version does not support EE 10.
