
## Restful Web Services:

      Restful Web Services is a stateless client-server architecture where web services are resources and can be identified by their URIs.

      REST Client applications can use HTTP GET/POST methods to invoke Restful web services. REST doesn’t specify any specific protocol to use,
      but in almost all cases it’s used over HTTP/HTTPS. When compared to SOAP web services, these are lightweight and doesn’t follow any standard.
      We can use XML,JSON, text or any other type of data for request and response.
      
      ### Java API for RESTful Web Services (JAX-RS) is the Java API for creating REST web services. its a part of JDK so you
      need to install any SW.
      
      Some of the important JAX-RS annotations are:

### @Path: used to specify the relative path of class and methods. We can get the URI of a webservice by scanning the Path annotation value.
### @GET, @PUT, @POST, @DELETE and @HEAD: used to specify the HTTP request type for a method.
### @Produces, @Consumes: used to specify the request and response types.
### @PathParam: used to bind the method parameter to path value by parsing it.
