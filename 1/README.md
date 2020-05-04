```
public class NumberGenerator{

    public static List<Integer> fibonacci(Integer n){
        List<Integer> returnList = new List<Integer>();

        Integer a = 0, b = 1; //Initial numbers and place holders
        Integer c; //new number place holder

        returnList.add(a);
        returnList.add(b);

        for(Integer i = 0; i < n-2; i++){

            c = a + b;
            returnList.add(c);
            a = b;
            b = c;
        }

        return returnList;
    }

    public static List<Integer> fibonacci(Integer starter, Integer sizer){
        List<Integer> returnList = new List<Integer>();

        Integer a = 1, b = starter; //Initial numbers and place holders
        Integer c = 0; //new number place holder

        returnList.add(a);
        returnList.add(b);

        for(Integer i = 0; i < sizer-2; i++){

            c = a + b;
            returnList.add(c);
            a = b;
            b = c;
        }

        return returnList;

    }

}
```
