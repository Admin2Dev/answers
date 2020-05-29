## NameChangerTest
```
@isTest
public class NameChangerTest {

    @testSetup static void insertingData(){
		 //Create test data
        List<Contact> finalList = new List<Contact>();
        for (Integer i = 1; i<=5; i++){
            Contact con = new Contact();
            con.lastName = 'Test';
            finalList.add(con);
        }
        for (Integer i = 1; i<=5; i++){
            Contact con = new Contact();
            con.lastName = 'Test 2';
            finalList.add(con);
        }

        insert finalList;
    }

    static testmethod void NameChangerTestMethod(){
        //execute batch in test()
        Test.startTest();
        NameChanger tester = new NameChanger();
        Id JobId = Database.executeBatch(tester);
        Test.stopTest();

        System.assertEquals(5, [SELECT count() FROM Contact WHERE LastName = 'Test' AND FirstName = 'Batch Test'], 'Failed Test Name Check');
        System.assertEquals(5, [SELECT count() FROM Contact WHERE LastName = 'Test 2' AND FirstName = 'Batch Test 2'], 'Failed Test Name 2 Check');
    }

}
```
