## OpenWeatherMap Test Class

```
@isTest
public class OpenWeatherMapTest {
    static testmethod void testerClass(){

        Test.setMock(HttpCalloutMock.class, new OpenWeatherMapMock()); //This line makes the call to mock response class

        System.assertEquals('At London, GB the weather is currently 11.43C or 52.574F. The weather seems broken clouds. Have a nice day!', OpenWeatherMap.getTemperature('London'));

    }

}
```
