# MSK-App

How can I extract ads form an ad site and view them in a flutter app? , the ad site has been made by the classified listing plugin in wordpress.


I have been trying to extract the data of all ads in an ad site and view them in a flutter app.
The ad site has been made by wordpress and its structure is maintained by the classified listing plugin (by RadiusTheme).
I use Postman app to test the api and make the get requests.
Here is the function I used in flutter to get the data:

    Future getDataFromServer(String url) async {
 
      var responseBody;

      var request = http.Request('GET', Uri.parse(url));

      http.StreamedResponse response = await request.send();

      if (response.statusCode == 200) {
        responseBody = jsonDecode(await response.stream.bytesToString());
        print(responseBody);
      } else {
        return response.reasonPhrase;
      }

      return responseBody;
    } 

Then I pass the url and get the data and present them in a list of widgets.
The url is like this : https://(siteurl)/wp-json/wp/v2/rtcl_listing?per_page=10
but the extension (*rtcl_listing*) doesn't present the ads with all the details in postman.
The details I mean are the title, the category, the image, the price and the location.

I was able to get the title and the image, but not the rest of the details.

what type of extension should I write after wp-json/wp/v2/  to get the ads with the desired details to present them in the flutter app?
