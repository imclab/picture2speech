# Visual-Eyes

Our vision is to make all images on the internet accessible to blind and partially sighted people. 

We have developed a web-service that provides meaningful  descriptions for online images, with an emphasis on social image sharing applications (Flickr, Facebook etc.). 

So using this webservice can determine that this photo has a boy and a girl, standing with a dog, on the sea beach with blue sky. Using social data where possbile we can mash up the names, relations and locations of people in the photos.

The service can also interface with screen reader, voice over services and embedded within browser extensions. 

For this prototype, we are utilising cloud based image processing apis from rekognition.com, iqengines.com and mash social data from Facebook.com. Our long term goal is to utilize open source technology and develop the necessary infrastructure and services to provide open apis. We are hosting all the code on Github. 

# Rekognition.com  - Face & scene detection
Detects and recognizes faces with guesstimations about gender, facial expressions and 
Recognizes common scenes - Nightlife, Beach, Urban etc.

See a working example at http://rekognition.com/demo/

# IQEngines.com - Object recognition

*objectQuery()*: 	Send an image to the IQ Engines server, which will extract
				its visual content
Parameters: Input image file name
Returns: Unique query id associated with the input image

*resultQuery()*: Request classification information for an image using unique identifier
				 that was generated when posting the image initially
Parameters: Unique image indentifier
Returns: Currenly plain json response from the server, containing all the useful bits

## API endpoints
We currently use only the following calls:

*queryApi*: http://api.iqengines.com/v1.2/query/
docs: https://www.iqengines.com/apidocs/apis/query-api.html

*resultApi*:  http://api.iqengines.com/v1.2/result/
docs https://www.iqengines.com/apidocs/apis/result-api.html

## API caveats
	1. Each API call should be associated with a unique api_sig hash
    2. api_sig is generated by hashing input variables in _alphabatical_ order
    3. The api_sig that is computed while posting an image to the server, needs to be
    	tracked as it is used as a unique identifier to fetch the results on that
    	image in all subsequent calls.
    4. Each and every api call should have its own unique api_sig.
    5. The query sends image as HTML multipart POST



# Generate the sentence (story) based on picture metadata

*generateStory()*: Request metadata from an image to train into a human readable sentence. Require further training the metadata from the community...  


# Transform the sentence into speech
  
 We are currently using built-in voiceOver function on mobile and desktop devices.


