## OpenWeatherMap
```
public class OpenWeatherMap {

	//Creating the JSON Structure

    public class JSONResponse{
        public List<Weather> weather;
        public sys sys;
        public string name; //city name
        public main main;

    }

    public class Weather {
        public String description; //description of weather
    }

    public class sys{
        public String country; //country name
    }

    public class main {
        public Decimal temp; //Temperature in Kelvin
    }



    public static String getTemperature(String city){ //get temp of a city
        String inputUrl = 'https://api.openweathermap.org/data/2.5/weather?q=' + city + '&appid=f335bb76cf2491f6faef107ae2c265f3'; //first build the URL
        return makeRequest(inputUrl);
    }

    private static String makeRequest(String inputUrl){

        String requestType = 'GET';

        //Build the request
        Http http = new Http();
        HttpRequest request = new HttpRequest();
        request.setEndpoint(inputUrl);
        request.setMethod(requestType);

        //Make the request
        HttpResponse response = http.send(request);

        //Deserialize the JSON
        JSONResponse result = (JSONResponse) JSON.deserialize(response.getBody(), JSONResponse.class);

        String finalString =  'At ' + result.name + ', ' + result.sys.country + ' the weather is currently ' + (result.main.temp - 273.15) + 'C or ' + ((result.main.temp - 273.15) * 9/5 + 32)+ 'F. The weather seems ' + result.weather[0].description + '. Have a nice day!';
        return finalString;
    }

}
```
