## [ApiController]

> Can be applied to a controller class to enable the following opinionated, API-specific behaviors:

1.  Attribute routing requirement:  `[Route]("api/[controller]")`
2.  Automatic HTTP 400 responses
3.  Binding source parameter inference: `[FromBody], [FromQuery]`
4.  Multipart/form-data request inference
5.  Problem details for error status codes

