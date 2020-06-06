## OpenWeatherMapMock

```
```
@isTest
global class OpenWeatherMapMock implements HttpCalloutMock {
	global HTTPResponse respond(HTTPRequest request) {

        String responseJSON = '{"coord":{"lon":-0.13,"lat":51.51},"weather":[{"id":803,"main":"Clouds","description":"broken clouds","icon":"04n"}],"base":"stations","main":{"temp":284.58,"feels_like":282.54,"temp_min":284.26,"temp_max":285.37,"pressure":998,"humidity":58},"wind":{"speed":0.89,"deg":274,"gust":4.02},"clouds":{"all":55},"dt":1591396997,"sys":{"type":3,"id":2019646,"country":"GB","sunrise":1591328769,"sunset":1591387939},"timezone":3600,"id":2643743,"name":"London","cod":200}';

        HttpResponse response = new Httpresponse();
        response.setStatusCode(200);
        response.setBody(responseJSON); //This is what the mock repsonse will be
        return response;
    }

}
```
