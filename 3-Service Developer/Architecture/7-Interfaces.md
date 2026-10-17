### Message Protocol

The X-Road Message Protocol is used by service client and service provider information systems for communicating with the X-Road Security Server.

X-Road supports two message protocols: [message protocol for SOAP](https://docs.x-road.global/Protocols/pr-mess_x-road_message_protocol.html) and [message protocol for REST](https://docs.x-road.global/Protocols/pr-rest_x-road_message_protocol_for_rest.html). Both protocols are synchronous, and they're initiated by the client IS or by the service provider's Security Server.

### Service Metadata Protocol

The X-Road Service Metadata Protocol can be used by the service client information systems to gather information about the X-Road instance. In particular, the protocol can be used to find X-Road members, services offered by these members and the WSDL / OpenAPI 3 service descriptions.

The X-Road Service Metadata Protocol has two versions: one for [SOAP](https://docs.x-road.global/Protocols/pr-meta_x-road_service_metadata_protocol.html) and another one for [REST](https://docs.x-road.global/Protocols/pr-mrest_x-road_service_metadata_protocol_for_rest.html). The SOAP version provides information about the available SOAP services only and similarly, the REST version contain information about the available REST services only. This means that in case information about all the available SOAP and REST services needs to be collected, both SOAP and REST versions of the metaservices must be invoked.

The protocol is synchronous RPC style protocol that is initiated by the service client IS.

### Downloading Signed Documents

The [signed document download service](https://docs.x-road.global/Manuals/ug-sigdoc_x-road_signed_document_download_and_verification_manual.html#2-signed-document-download-servicehttps://docs.x-road.global/Manuals/ug-sigdoc_x-road_signed_document_download_and_verification_manual.html#2-signed-document-download-service) can be used by the information systems to download signed ASiC containers from the Security Server's message log. The containers can be transferred to third parties and verified offline. In addition, the service provides a convenience method for downloading global configuration that is required for verifying the containers.

The containers can be verified using the [signed document verification tool](https://docs.x-road.global/Manuals/ug-sigdoc_x-road_signed_document_download_and_verification_manual.html#3-signed-document-verification-tool) - the asicverifier command line utility. The asicverifier utility is shipped with the Security Server and in addition to the verification, it can be used to extract signed files from the containers.

The protocol is a synchronous RPC-style protocol that is initiated by the IS.

### Operational Monitoring Protocol

The X-Road [Operational Monitoring Protocol](https://docs.x-road.global/OperationalMonitoring/Protocols/pr-opmon_x-road_operational_monitoring_protocol_Y-1096-2.html) can be used by the external monitoring systems to gather operational information of the Security Server. The protocol is synchronous RPC style protocol that is initiated by the external monitoring system.

### Environmental Monitoring Protocol

The [Environmental Monitoring Protocol](https://docs.x-road.global/EnvironmentalMonitoring/Monitoring-messages.html) can be used by the external monitoring systems to gather environmental monitoring information about the Security Server.