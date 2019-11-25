# JAX-WS Tracer V1.0

## Description
The implementation of com/sun/xml/ws/client/RequestContext.java changed in jaxws-rt v2.2.6. The tracer in this field pack replaces the OOTB tracer provided with the CA APM SOA Performance Management (SPM) extension.
Use this field pack if you are using jaxws-rt v2.2.6 and see this error message in you logs:
``java.lang.ClassCastException: java.util.HashMap cannot be cast to com.sun.xml.ws.transport.Headers
                at com.sun.xml.ws.client.RequestContext.fill(RequestContext.java:339)
                at com.sun.xml.ws.client.Stub.configureRequestPacket(Stub.java:454)``

Provide a short description of the field pack here. See [Mastering Markdown](https://guides.github.com/features/mastering-markdown/) for markdown syntax.

## Short Description
This field pack replaces the OOTB tracer provided with the CA APM SOA Performance Management (SPM) extension for jaxws-rt v2.2.6.

## APM version
Tested with APM 9.5.

## Supported third party versions
jaxws-rt v2.2.6

## Limitations
none

## License
Eclipse Public License - v 1.0

# Installation Instructions

## Prerequisites
none

## Dependencies
APM agent 9.1+, SOA (web services) extension 9.1+

## Installation
Copy ``ca.apm.fieldpacks.jaxws-tracer.jar`` into ``core/ext`` folder of CA APM java agent.

## Configuration
Replace the following lines in spm-correlation.pbd (then you won't need jax-ws.pbd).
SetTracerClassMapping: WL_CLIENT_JAXWS_CorrelationTracer ``com.wily.powerpack.webservices.extension.agent.trace.weblogic.SEIStubCorrelationTracer com.wily.introscope.probebuilder.validate.ResourceNameValidator``
with
``SetTracerClassMapping: WL_CLIENT_JAXWS_CorrelationTracer ca.apm.fieldpacks.trace.weblogic.SEIStubCorrelationTracer com.wily.introscope.probebuilder.validate.ResourceNameValidator``
Restart your application server.

# Usage Instructions
n/a

## Metric description
n/a. This tracer does not generate any metrics. It only allows for cross process correlation when you are using jaxws-rt v2.2.6.

## Custom Management Modules
n/a

## Custom type viewers
n/a

## Name Formatter Replacements
n/a

## Debugging and Troubleshooting
Set agent log level to DEBUG.

## Support
This document and associated tools are made available from CA Technologies as examples and provided at no charge as a courtesy to the CA APM Community at large. This resource may require modification for use in your environment. However, please note that this resource is not supported by CA Technologies, and inclusion in this site should not be construed to be an endorsement or recommendation by CA Technologies. These utilities are not covered by the CA Technologies software license agreement and there is no explicit or implied warranty from CA Technologies. They can be used and distributed freely amongst the CA APM Community, but not sold. As such, they are unsupported software, provided as is without warranty of any kind, express or implied, including but not limited to warranties of merchantability and fitness for a particular purpose. CA Technologies does not warrant that this resource will meet your requirements or that the operation of the resource will be uninterrupted or error free or that any defects will be corrected. The use of this resource implies that you understand and agree to the terms listed herein.

Although these utilities are unsupported, please let us know if you have any problems or questions by adding a comment to the CA APM Community Site area where the resource is located, so that the Author(s) may attempt to address the issue or question.

Unless explicitly stated otherwise this field pack is only supported on the same platforms as the APM core agent. See [APM Compatibility Guide](http://www.ca.com/us/support/ca-support-online/product-content/status/compatibility-matrix/application-performance-management-compatibility-guide.aspx).

### Support URL
https://github.com/CA-APM/fieldpack.jaxws-tracer/issues

## Categories
Frameworks

# Change log
Changes for each version of the field pack.

Version | Author | Comment
--------|--------|--------
1.0 | Guenter Grossberger | First version of the field pack.
