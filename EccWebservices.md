# ECCWebservices notes

## Example of using a Spring environment variable
```
@Value("${iplus.environment}")  // Taken from application-eccLocal.properties.  Configured by Spring.
  private String environment;
```

## Using environmental resources folder
In resources folder, have different environmnetal properties folders, for application-eccLocal.properties for example.

## Swagger
Below is the interface needed for Swagger endpoints.  Also needs the SwaggerConfig class.
See the Swagger endpoints at:  http://localhost:9000/swagger-ui.html#/

```
/**
 * Marks an endpoint as belonging to APC application
 * Any method annotated as an endpoint which also includes this annotation will
 * be included in the swagger report when it runs on the host where the
 * endpoints are being hosted.
 */

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface DocumentRestEndpoint {
}

```

##Main SpringBoot Applications
A EccWebservicesApplication has the psvm method, which bootstraps the application.  

##Backendutilities 
The `ReturnCode` class is a good example of an enum with methods:

```aidl
import java.util.LinkedHashMap;
import java.util.Map;

public class ReturnCode {

  public enum ReturnCodeStatus {
    ERROR,
    WARN,
    OK;

    public boolean isOk() {
      return this.equals(OK);
    }

    public boolean isError() {
      return this.equals(ERROR);
    }
  }

  // map for policy branch and I+ environment
  private static final Map<String, ReturnCodeStatus> returnCodeStatusMap = new LinkedHashMap<>();

  static {
    // "Good" return - you can carry on
    returnCodeStatusMap.put("0", ReturnCodeStatus.OK);
    // "Error" return - the request for data has failed, you cannot carry
    // on, abort
    returnCodeStatusMap.put(null, ReturnCodeStatus.ERROR);
    returnCodeStatusMap.put("", ReturnCodeStatus.ERROR);
    returnCodeStatusMap.put("S", ReturnCodeStatus.ERROR);
    returnCodeStatusMap.put("E", ReturnCodeStatus.ERROR);
    returnCodeStatusMap.put("W", ReturnCodeStatus.WARN);
    returnCodeStatusMap.put("I", ReturnCodeStatus.WARN);
  }

  /**
   * .
   * @param returnCode .
   * @return .
   */
  public static ReturnCodeStatus translateAs400ReturnCode(String returnCode) {
    if (returnCode != null) {
      returnCode = returnCode.trim();
    }
    return returnCodeStatusMap.get(returnCode);
  }

}
```

The `ParameterConverter` class is a way to ensure that program parameters are correctly converted to IBMi acceptable
parameters.  

The `CallAS400Program` accepts the configured program from the properties file, and 





##Utils folder
Use a utils folder for all miscellaneous code, convert to date type, pad policy number etc...
