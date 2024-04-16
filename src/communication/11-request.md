# HTTP Request

## Terms

### QueryString

The HTTP query string is specified by the values following the question mark (?).

Query strings are contained in request headers. It is wise to not trust the data that is contained in headers, as this information can be falsified by malicious users.

As a security precaution, always encode header data or user input before using it. Alternatively, you can validate header data and user input with a short function.

## References

* Book : [Writing Secure Code](https://www.amazon.com/Writing-Secure-Second-Developer-Practices/dp/0735617228), 2nd edition
* Microsoft | [Request object](https://learn.microsoft.com/en-us/previous-versions/iis/6.0-sdk/ms524948(v=vs.90))
