Trackingmore-NODEJS
=================

The NODEJS SDK of Trackingmore API
## Official document

[Document](https://www.trackingmore.com/v3/api-index)

##Init

```
const apiKey = 'you api key';
const tracker = new Tracking(apiKey);
async function getData(url, data, method) {
    let res = await tracker.doRequest(url, data, method);
    return res;
}
```

Quick Start
--------------
- Put your ApiKey in the constructor of the Api class
- All returns are in Json format String.
- After instantiating the Api class, you can use its interface methods
- Most Api params receive multiple tracking numbers

**Get a list of the couriers in Trackingmore**

	getData('courier', post_data, 'POST')

**Detect which couriers defined in your account match a tracking number**

	post = { "tracking_number": 'EA152563254CN' }
    getData('detect', post, 'POST')


**Post trackings to your account**

    //Create single tracking numbers
    post_data  = {"tracking_number": "EA152563254CN", "courier": "china-ems"}
    //Create multiple tracking numbers
    post_data  = [{"tracking_number": "EA152563254CN", "courier": "china-ems"},{"tracking_number": "EA152563254CN", "courier": "china-ems"}]
     getData('create', post_data, 'POST')

**Summary of Connection API Methods with all the api and Methods**

           //count
    count = 'count?courier=1&limit=100&created_at_min=1521314361&created_at_max=1541314361'
    getData(count).then(r => {
    console.log(r)
    });
    
    //
    
    // // Get tracking results of a  tracking or List all trackings
    // get = 'get?page=1&limit=100&created_at_min=1521314361&created_at_max=1541314361'
    // getData(get)
    
    
    // post_data = [{ "tracking_number": 'EA152563254CN', "courier_code": 'china-ems' }, { "tracking_number": 'EA152563254CN', "courier_code": 'china-ems' }]
    // Update Tracking item
    // getData('modifyinfo', post_data, 'PUT')
    
    //
    // archive
    // getData('archive', post_data, 'POST')
    
    //
    // // Delete tracking item
    // getData('delete', post_data, 'DELETE')
    
    //
    // // create  tracking number
    // getData('create', post_data, 'POST')
    
    //
    // // manual update
    // getData('manualupdate', post_data, 'POST')
    
    //
    // // remote tracking
    // getData('remote', post_data, 'POST')
    
    //
    // // Get cost time iterm results
    // getData('transittime', post_data, 'POST')
    
    //
    // // detect a carriers by tracking number
    // post = { "tracking_number": 'EA152563254CN' }
    // getData('detect', post, 'POST')
    
    //
    // // get all carriers
    // getData('courier')
    
    //
    // // Get status number
    // status = 'status?tracking_number=EA152563254CN'
    // getData(status)
    
    //
    // // Set number not update
    // getData('notupdate', post_data, 'POST')
    
    //
    // // Modify courier code
    // post = { "tracking_number": 'EA152563254CN', "courier_code": 'china-ems', "new_courier_code": 'china-post' }
    // getData('modifycarrier', post, 'PUT')
    //
    // Get user info
    // getData('getuserinfo')
    //
    // // air real time track
    // getData('aircargo', post_data, 'POST')

## Typical Server Responses

We will respond with one of the following status codes.

Code|Type | Message
----|--------------|-------------------------------
200    | <code>Success</code>|    Request response is successful
203    | <code>PaymentRequired</code>|  API service is only available for paid account Please subscribe paid plan to unlock API services                                                             ul
204    | <code>No Content</code>|    Request was successful, but no data returned Tracking NO. or target data possibly do not exist
400    | <code>Bad Request</code>| Request type error Please check the API documentation for the request type of this API
401    | <code>Unauthorized</code>|    Authentication failed or has no permission Please check and ensure your API Key is correct
403    | <code>Bad Request</code>|    Page does not exist Please check and ensure your link is correct                                                                                             ul
404    | <code>Not Found</code>|    Page does not exist Please check and ensure your link is correct
408    | <code>Time Out</code>|    Request timeout The official website did not return data, please try again later
411    | <code>Bad Request</code>|    Specified request parameter length exceeds length limit Please check and ensure that the request parameters are of the required length
412    | <code>Bad Request</code>|    Specified request parameter format doesn't meet requirements Please check and ensure that the request parameters are in the required format
413    | <code>Out limited</code>|    The number of request parameters exceeds the limit Please check the API documentation for the limit of this API
417    | <code>Bad Request</code>|    Missing request parameters or request parameters cannot be parsed Please check and ensure that the request parameters are complete and correctly formatted
421    | <code>Bad Request</code>|    Some of required parameters are empty Some couriers need special parameters to track logistics information (Special Couriers)
422    | <code>Bad Request</code>|    Unidentifiable courier code Please check and ensure that the courier code are correct(Courier code)
423    | <code>Bad Request</code>|    Tracking No. already exists
424    | <code>Bad Request</code>|    Tracking No. no exists Please use 「Create trckings」 API first to create trackings
429    | <code>Bad Request</code>|    Exceeded API request limits, please try again later Please check the API documentation for the limit of this API
511    | <code>Server Error</code>|    Server error Please contact us: service@trackingmore.org.
512    | <code>Server Error</code>|    Server error Please contact us: service@trackingmore.org.
513    | <code>Server Error</code>|    Server error Please contact us: service@trackingmore.org.        